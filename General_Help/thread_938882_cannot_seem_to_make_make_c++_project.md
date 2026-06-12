---
title: "cannot seem to make make c++ project"
date: 2008-10-05
forum: General Help
---

### Post by tb189 on 2008-10-05
I'm pretty new to this scene, and I've been following tutorials on how to get a C++ file to build and run on the CDT plugin for eclipse. I think this just uses make and g++. If I make I get the following error: 

main.o: In function `std::__verify_grouping(char const*, unsigned int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
/usr/include/c++/4.2/bits/locale_facets.tcc:2562: undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::size() const'
.... (it goes on in similiar fashion)


My source file is:

#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
        cout << "Hello World" << endl;
        return 0;
}


My makefile is:

main: main.o
	g++ -o main.out main.o
	
main.o: main.cpp
	g++ -c main.cpp
	
clean:
	rm main.o main.out

Can any one tell me what I'm doing wrong? Thanks!

---

