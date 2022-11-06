# max_heap_py
````py
class MaxHeap:
    def __init__(self, arr):
        self.arr = arr
        self.n = len(arr)
    def insert(self, value):
        self.arr.append(value)
        self.n +=1
        self.heapfiy_up(self.n - 1)

    def delete(self):
        self.arr[0], self.arr[self.n - 1] = self.arr[self.n - 1], self.arr[0]
        self.arr.pop()
        self.n -= 1
        self.heapify_down(0)



    def heapify_down(self, i):
        lc, rc = i * 2 + 1, i * 2 + 2
        largestValue, largestIndex = self.arr[i], i
        if lc < self.n and self.arr[lc] > largestValue:
            largestValue, largestIndex = self.arr[lc], lc
        if rc < self.n and self.arr[rc] >largestValue:
            largestValue, largestIndex = self.arr[rc], rc
        if largestIndex != i:
            self.arr[i], self.arr[largestIndex] = self.arr[largestIndex], self.arr[i]
            self.heapify_down(largestIndex)

    def heapfiy_up(self, i):
        parent = (i - 1) // 2
        if parent >= 0 and self.arr[i] > self.arr[parent]:
            self.arr[i], self.arr[parent] = self.arr[parent], self.arr[i]
            self.heapfiy_up(parent)

    def build_heap(self):
        last_non_leaf = self.n // 2 - 1
        for i in range(last_non_leaf, -1, -1):
            self.heapify_down(i)

    def heapsort(self):
        for i in range(self.n - 1):
            self.arr[0], self.arr[self.n - 1] = self.arr[self.n - 1], self.arr[0]
            self.n -= 1
            self.heapify_down(0)
        return self.arr
#insertion
# heap = MaxHeap([220, 190, 180, 175, 181, 120, 170, 160, 170])
# heap.insert(200)
# heap.insert(100)
# print(heap.arr)

#deletion
# heap = MaxHeap([100, 90, 80, 70, 60])
# heap.delete()
# heap.delete()
# print(heap.arr)

# build heap
# heap = MaxHeap([1,3,5,4,6,13,10,9,8,15,7])
# heap.build_heap()
# print(heap.arr)

# heapsort
heap = MaxHeap([220, 190, 180, 175, 181, 120, 170, 160, 170])
heap.heapsort()
a= heap.heapsort()[::-1]
print(a)

````
