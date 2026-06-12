---
title: "Structure definition in C"
date: 2008-10-16
forum: General Help
---

### Post by csnerdliz on 2008-10-16
I am trying to implement the vector in C for a programming project. I declare the vector struct in my .h file and then try to access its fields in the .c file. I did declare a variable of type vector. However, I get a compiler error saying that 'vector has no member named' [x] where x is the fields I defined in my struct. Here is my struct def in the .h file: 
typedef struct {
  void* elems;
  int elemSize;
  int logLength;
  int allocLength;
} vector;

---

### Post by Slim Odds on 2008-10-16
[http://www.cprogramming.com/](http://www.cprogramming.com/)

---

