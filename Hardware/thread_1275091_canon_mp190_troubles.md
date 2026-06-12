---
title: "canon mp190 troubles"
date: 2009-09-25
forum: Hardware
---

### Post by gwydionwaters on 2009-09-25
hello all,
i have a ppc g4 laptop, running ubuntu 8.10. my printer is a canon mp190, my os recognizes it but only has support for the 180 which does not have a scanner. i found the driver for linux on canon-europe and it comes with two .debs, one main and one common libs. also one tar with source, seemingly only for the common libraries. unfortunately no instructions. i have put the tar with printer files [here]("http://www.robloranger.ca/files/shared/MP190_debian_printer.tar"), sorry it is a bit biggish - 7.6MB... the scanner is separate but i will work with one at a time [IMG]http://e1h7.simplecdn.net/lqcdn/images/questions/images/smilies/smile.gif[/IMG] any ideas how to use this with my architecture? i did try dpkg --force-architecture and it worked but when i try to print i get errors and no printing. the cups debugging file is [here]("http://www.robloranger.ca/files/shared/troubleshoot.txt")

---

### Post by gwydionwaters on 2009-09-25
i have so far removed the forced debs and gone with the source, i originally avoided it because it does not seem as friendly as the average source. the make file does nothing in the main directory, it looks like this ```
#dirs = libs cngpij cngpijmon ppd pstocanonij 
dirs = libs cngpij pstocanonij backend

scripts=for dir in $(dirs); do\
            (cd $$dir; make $$target)|| exit 1;\
        done

all :
    $(scripts)

clean :
    target=clean; $(scripts)

install :
    target=install; $(scripts)

```so going into the dirs that are not commented out at the top, there are autogen.sh files which seem to work for libs but when i get to cngpij i get through the autogen but the make outputs ```
Making install in cngpij
make[1]: Entering directory `/home/rob/cnijfilter-common-3.00/cngpij/cngpij'
gcc -DHAVE_CONFIG_H -I. -I..    -O2 -Wall -I../include/cncl -I../include/misc -I../../libs/paramlist -O2 -MT bjcups.o -MD -MP -MF .deps/bjcups.Tpo -c -o bjcups.o bjcups.c
bjcups.c:25:23: error: cups/cups.h: No such file or directory
bjcups.c:26:22: error: cups/ppd.h: No such file or directory
bjcups.c: In function &#8216;add_option_param&#8217;:
bjcups.c:189: warning: implicit declaration of function &#8216;strlen&#8217;
bjcups.c:189: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
bjcups.c: In function &#8216;add_option_param_bl&#8217;:
bjcups.c:198: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
bjcups.c: In function &#8216;add_option_value&#8217;:
bjcups.c:207: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
bjcups.c: In function &#8216;add_option_string&#8217;:
bjcups.c:215: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
bjcups.c: In function &#8216;init_option&#8217;:
bjcups.c:242: warning: implicit declaration of function &#8216;strdup&#8217;
bjcups.c:242: warning: incompatible implicit declaration of built-in function &#8216;strdup&#8217;
bjcups.c:248: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
bjcups.c: In function &#8216;parse_product_name&#8217;:
bjcups.c:278: warning: implicit declaration of function &#8216;memset&#8217;
bjcups.c:278: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
bjcups.c: In function &#8216;get_product_name&#8217;:
bjcups.c:296: warning: implicit declaration of function &#8216;cupsGetPPD&#8217;
bjcups.c:296: warning: initialization makes pointer from integer without a cast
bjcups.c:305: error: &#8216;ppd_file_t&#8217; undeclared (first use in this function)
bjcups.c:305: error: (Each undeclared identifier is reported only once
bjcups.c:305: error: for each function it appears in.)
bjcups.c:305: error: &#8216;p_ppd&#8217; undeclared (first use in this function)
bjcups.c:307: warning: implicit declaration of function &#8216;ppdOpenFile&#8217;
bjcups.c:309: warning: implicit declaration of function &#8216;strcmp&#8217;
bjcups.c:312: warning: implicit declaration of function &#8216;strncpy&#8217;
bjcups.c:312: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
bjcups.c:314: warning: implicit declaration of function &#8216;ppdClose&#8217;
bjcups.c: In function &#8216;main&#8217;:
bjcups.c:573: warning: implicit declaration of function &#8216;cupsGetDefault&#8217;
bjcups.c:573: warning: assignment makes pointer from integer without a cast
bjcups.c:574: warning: incompatible implicit declaration of built-in function &#8216;strdup&#8217;
bjcups.c:588: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
bjcups.c:589: warning: implicit declaration of function &#8216;strcpy&#8217;
bjcups.c:589: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
bjcups.c:590: warning: implicit declaration of function &#8216;strcat&#8217;
bjcups.c:590: warning: incompatible implicit declaration of built-in function &#8216;strcat&#8217;
bjcups.c:615: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
make[1]: *** [bjcups.o] Error 1
make[1]: Leaving directory `/home/rob/cnijfilter-common-3.00/cngpij/cngpij'
make: *** [install-recursive] Error 1

```

what does this mean? i have both libcups and libpopt-dev installed and up to date.

---

