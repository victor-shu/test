#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

bool isIn(vector<int> v, int i)
{
  for(int x : v)
  {
    if(x==i)
      return true;
  }
  return false;
}

class Graph
{
    int V;
    std::vector<int> *adj;
    std::vector<int> vertex;
    std::vector<std::vector<int>> dists;
public:
    Graph(int V);
    void addEdge(int v, int w, int distance);
    int distance(int v, int w);
    int distOfPath(std::vector<int> path);
    vector<int> dfs(bool used[], int curr, vector<int> path);
    vector<int> ddffss(int curr);
};
Graph::Graph(int V)
{
    this->V = V;
    adj = new std::vector<int>[V];
    dists.resize(V);
    for(int i = 0; i<V; i++)
    {
      dists[i].resize(V);
    }
}
void Graph::addEdge(int v, int w, int distance)
{
    adj[v].push_back(w);
    adj[w].push_back(v);
    dists[v][w] = distance;
    dists[w][v] = distance;
    if(!isIn(vertex, v))
      vertex.push_back(v);
    if(!isIn(vertex, w))
      vertex.push_back(w);
}
int Graph::distance(int v, int w)
{
  return dists[v][w];
}
int Graph::distOfPath(std::vector<int> path)
{
  int dis = 0;
  for(int i = 1; i < path.size(); i++)
  {
    dis += distance(path[i], path[i-1]);
  }
  return dis;
}


std::vector<int> Graph::dfs(bool used[], int curr, std::vector<int> path)
{
	bool visited[V];
	std::copy(used, used+V, visited);
	visited[curr] = true;
	path.push_back(curr);

	int done = true;
	for (int i = 0; i < V; i++)
	{
		if (!visited[i])
		{
			done = false;
			break;
		}
	}
	if (done)
	{
		return path;
	}

	std::vector<int> min;
	for (int i = 0; i < V; i++)
	{
		if (!visited[i])
		{
			vector<int> result = dfs(visited, i, path);
			if (distOfPath(min) > distOfPath(result))
			{
				min = result;
			}
		}
	}
	return min;
}
void print(vector<int> v)
{
  for(int i : v)
  {
    cout<<i<<"  ";
  }
}
vector<int> Graph::ddffss(int curr)
{
  bool x[V];
  for(int i = 0; i < V; i++)
  {
    x[i] = false;
  }
  vector<int> path;
  return dfs(x, curr, path);
}
int main()
{

  Graph g(4);
  g.addEdge(0, 1, 1);
  g.addEdge(0, 2, 2);
  g.addEdge(0, 3, 3);
  g.addEdge(1, 2, 4);
  g.addEdge(1, 3, 5);
  g.addEdge(2, 3, 6);

  print(g.ddffss(0));

  return 0;
}
