---
title: "How to get multiverse repository offline?"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Gagansharma200 on 2009-05-06
Hi , I am new to Ubuntu (and to Linux),but highly inspired by free software.
I have no connectivity to internet at home, but want to enjoy softwares from various 
software bins (Multiverse,Universe e.t.c..).
After some reading over internet I have found , Images of these are  available on DVD.
I am not sure how to obtain those DVD and how much these will cost to me .
Can someone guide me in this regard?
I am living in India.
 
:confused:

---

### Post by Partyboi2 on 2009-05-06
Hi, have a look at [http://www.zyxware.com/requestcd](http://www.zyxware.com/requestcd) looks like you can get the repos for hardy or intrepid if you live in India.
Another useful tool if you want to update your ubuntu is to use [[COLOR=Blue]keyrx[/COLOR]]("http://keryxproject.org/") which allows you to download the packages you want from another machine that has access to the Internet.

---

### Post by Gagansharma200 on 2009-05-06
Hi Partiboi2,
                 I have read about both and [[COLOR=blue]keyrx[/COLOR]]("http://keryxproject.org/") suite me best.but before that i want to install UI
component for [[COLOR=blue]keyrx[/COLOR]]("http://keryxproject.org/"),how to do that?
Can you point to some good tutorial in this regard?

---

### Post by Partyboi2 on 2009-05-06
[[COLOR=Blue]Here[/COLOR]]("http://crashsystems.net/2009/01/keryx-tutorial/") is a tutorial on using keryx. Let us know how you go.

---

### Post by EXCiD3 on 2009-05-06
To use the UI on Linux, you must install python-wxversion, python-wxgtk2.8, libwxgtk2.8-0, and libwxbase2.8-0. These are the only 4 packages you need. It will really only help you create the projects graphically as Keryx is unable to install the packages just yet. 

I'll be working on Keryx 1.0 this summer which will be written from the ground up, making everything simpler and much quicker as well as a single-file executable for Windows and Linux (with hopefully a Mac one later on). 1.0 will install packages and everything else under the sun. :D (Don't quote me on that when release comes)

---

