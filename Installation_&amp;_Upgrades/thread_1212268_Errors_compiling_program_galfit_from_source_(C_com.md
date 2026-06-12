---
title: "Errors compiling program galfit from source (C compiler issue?)"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by Shockburner on 2009-07-13
Hi,
 I'm pretty new to Ubuntu, just a few weeks in.
 

 Anyways I have been unsuccessfully trying to compile a program called &#8220;galfit&#8221; which was written in C. Whenever I try to compile it I get several errors (listed below) that seem to be relate to my C complier or gcc. I have already installed &#8220;build-essential&#8221; and I have the latest version of gcc. Galfit is a relativity old program and and it is possible that my version of gcc is too new. When I compile galfit (using &#8220;make&#8221;) it does create a binary, however it does not work properly. Does anybody have any ideas how to solve my problem?

  	 	 	 	 	 	  EDIT: I have successfully compiled this program on a computer at work which has some version of redhat and GCC 3.4.6 but not on my Ubuntu :( .
 

 galfit.c: In function &#8216;blank_img&#8217;: 
 galfit.c:284: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;int *&#8217; 
 galfit.c:284: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;int *&#8217; 
 galfit.c:284: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 5 has type &#8216;int *&#8217; 
 galfit.c:284: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 6 has type &#8216;int *&#8217; 
 

 read_input.c: In function &#8216;checkpar&#8217;: 
 read_input.c:130: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 4 has type &#8216;char (*)[1025]&#8217; 
 read_input.c:150: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 4 has type &#8216;char (*)[10]&#8217; 
 

 nrutil.c: In function &#8216;nrerror&#8217;: 
 nrutil.c:37: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result 
 

 outmodel.c: In function &#8216;outmodel&#8217;: 
 outmodel.c:92: warning: format not a string literal and no format arguments 
 

 keypoll.c: In function &#8216;keypoll&#8217;: 
 keypoll.c:27: warning: ignoring return value of &#8216;scanf&#8217;, declared with attribute warn_unused_result 
 

 fourier.c: In function &#8216;fourier_pars&#8217;: 
 fourier.c:18: warning: format &#8216;%c&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;char (*)[10]&#8217; 
 

 edgedisk.c: In function &#8216;edgedisk&#8217;: 
 edgedisk.c:150: warning: incompatible implicit declaration of built-in function &#8216;fminf&#8217; 
 

 bending.c: In function &#8216;bending_pars&#8217;: 
 bending.c:18: warning: format &#8216;%c&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;char (*)[10]&#8217; 
 

 initcurses.c: In function &#8216;initcurses&#8217;: 
 initcurses.c:65: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result 
 initcurses.c: In function &#8216;port_search&#8217;: 
 initcurses.c:112: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 4 has type &#8216;char (*)[200]&#8217; 
 initcurses.c:103: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result 
 initcurses.c:120: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result

---

### Post by Partyboi2 on 2009-07-14
Hi, try using the binary one for debian, download it from [[COLOR=Blue]here[/COLOR]]("http://users.ociw.edu/peng/work/galfit/galfit-debian.tar")
then change into the directory where the downloaded file is and extract it.
```
tar xvzf galfit-debian.tar
```
Then make the extracted file executable
```
chmod +x galfit
```then start it with
```
 ./galfit
```

---

### Post by renbla on 2009-07-14
Yeah... Using deb is always the best option if you are not a developer :lolflag:

---

### Post by Shockburner on 2009-07-21
I tried that and it wasn't working for me but I was able to compile the source by using GCC 3.4 and that worked.

---

