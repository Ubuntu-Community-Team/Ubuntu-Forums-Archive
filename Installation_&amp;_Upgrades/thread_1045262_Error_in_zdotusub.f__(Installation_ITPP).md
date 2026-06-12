---
title: "Error in zdotusub.f ? (Installation ITPP)"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by tyelemou on 2009-01-20
Hi
I need help 
In installation of my IT++ on my PC Toshiba Intel on Ubuntu 8.10 
I thing all library is  
The error after tape : make 
 
zdotusub: 
Bareword found where operator expected at -e line 1, near "/itpp/base" 
(Missing operator before base?) 
String found where operator expected at -e line 1, at end of line 
(Missing semicolon on previous line?) 
syntax error at -e line 1, near "/itpp/base" 
Can't find string terminator '"' anywhere before EOF at -e line 1. 
/usr/bin/f77: aborting compilation 
make[4]: *** [zdotusub.lo] Error 1 

The code of the file zdotusuf is : 
subroutine zdotusub(dotu,n,x,incx,y,incy)
c
      external zdotu
      double complex zdotu,dotu
      integer n,incx,incy
      double complex x(*),y(*)
c
      dotu=zdotu(n,x,incx,y,incy)
      return
      end
I don't know fortran code

Thank you

---

