# codes_for_practice

幅優先探索を使って解く。  
交差点を点，交差点と交差点の間を辺とみれば，交差点Aを始点とする単一始点最短経路問題に帰着する。  
このとき，グラフは各辺のパスコストが互いに等価な正の値を持つ。  
負のコストをもつ辺のないグラフの単一始点最短経路問題を効率的に解くアルゴリズムとしてダイクストラ法がある。  
優先度付きキューを使うダイクストラ法は最短経路コストが更新された点をキューに格納する。  
そして経路が最も短い点をキューから取り出し，取り出された点に隣接する点の最短経路コストを可能であれば更新する。  
辺のコストが互いに等しい正の値となるとき，一つ点に対して最短経路コスト更新が1回しか起こらない。  
このとき，優先度付きキューではなくFIFOのキューを使うことができるので，  
次のアルゴリズムはダイクストラ法を使った場合と等価な結果をえることができる。  
このアルゴリズムの計算量は線形である。  
計算量が定数である単一始点最短経路問題を解くアルゴリズムは知られていないので，このアルゴリズムは効率がいいといえる。

```
queue.enqueue(s); // s is the start vertex.
distance[s] = 0;
consume(s); // mark s as a consumed vertex.

while(queue is not empty) {
  v = queue.dequeue
  for(v' <- v.neighbors) {
    if (v' is not consumed) {
      distance[v'] = distance[v'] + 1
      consume(v')
      queue.enqueue(v')
    }
  }
}

return distance[g] // g is the goal;
```
