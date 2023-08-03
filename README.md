Explain your approach in **three sentences only** at top of your code

# Design-1

## Problem 1:(https://leetcode.com/problems/design-hashset/)

## TC O(1), SC O(1)

class MyHashSet:

    def __init__(self):
        self.buckets = 1000
        self.bucketItems = 1000
        self.storage = [None] * self.buckets
    
    def getBucket(self, key: int) -> int:
        return key % self.buckets
    
    def getBucketItem(self, key: int) -> int:
        return key // self.bucketItems

    def add(self, key: int) -> None:
        bucket = self.getBucket(key)
        bucketItem = self.getBucketItem(key)

        if self.storage[bucket] == None:
            if bucket == 0:
                self.storage[bucket] = [None] * (self.bucketItems + 1)
            else:
                self.storage[bucket] = [None] * self.bucketItems

        self.storage[bucket][bucketItem] = True

    def remove(self, key: int) -> None:
        bucket = self.getBucket(key)
        bucketItem = self.getBucketItem(key)

        if self.storage[bucket] == None:
            return
        
        self.storage[bucket][bucketItem] = None
        
    def contains(self, key: int) -> bool:
        bucket = self.getBucket(key)
        bucketItem = self.getBucketItem(key)

        if self.storage[bucket] == None:
            return False

        return self.storage[bucket][bucketItem] == True
        


# Your MyHashSet object will be instantiated and called as such:
# obj = MyHashSet()
# obj.add(key)
# obj.remove(key)
# param_3 = obj.contains(key)

## Problem 2: Design MinStack (https://leetcode.com/problems/min-stack/)

# TC = O(1), SC = O(1)
class MinStack:

    def __init__(self):
        self.stack = []
        self.min = int(sys.maxsize)
        
    def push(self, val: int) -> None:
        if val <= self.min:
          self.stack.append(self.min)
          self.min = val
        self.stack.append(val)

    def pop(self) -> None:
        popped = self.stack.pop()
        if popped == self.min:
            self.min = self.stack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.min


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()


