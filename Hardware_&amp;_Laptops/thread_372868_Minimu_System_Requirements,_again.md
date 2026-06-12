---
title: "Minimu System Requirements, again"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by Linux4Larry on 2007-02-28
I have a Pentium (perhaps Celeron) 500MHz CDU, 20GB HDD, with 368 MB of RAM. 

I am running Xubuntu 6.10 Edgy Eft, can access the internet and I am running slimserver software to stream music to my stereo. Theoretically, my system should be plenty to run Xubuntu, which seems to only impose the requirements of more than 192 MB of RAM and 1.5GB of HDD.  

Also, FWIW, at this time, my primary intention is to stream music wirelessly to my stereo (slimserver for my Squeezebox). But I occasionally want to surf the web with Firefox, check Email with Thunderbird. 

What's strange is that some applications take minutes to load up, e.g. Synaptic Program Manager, it takes Firefox fifteen to thirty seconds to open, ABI office takes about thirty seconds to load. Even so, web pages load reasonably quickly, e.g. ten to thirty seconds. 

Any thoughts on what that system might be missing to run faster? FWIW, I notice that the system is noticeably slower with two or three applications open, e.g. Firefox, an open terminal and SPM. Is there a resident software program that can tell me how much RAM is being addressed? I'm wondering since another poster indicated that some of his RAM failed on him. If necessary, I'd be willing to buy a used computer with higher spec'd equipment, in which case I'd like suggestions for better performance.

Your constructive thoughts are appreciated.
Thanks.
Larry

---

### Post by Majin Zero on 2007-03-16
Better CPU or faster Bus speeds on the mainboard and RAM, really things that are a waste to upgrade since you're pretty much redoing the computer.

---

### Post by dbott67 on 2007-03-16
I had 6.06 (as well as previous versions 4.10, 5.04, 5.10) running on a Toshiba Tecra 8000 laptop (P2-300 w/256 MB RAM).  Performance was reasonable, however, apps like Firefox and OpenOffice really bogged things down.

Opera was bar far the fastest browser and AbiWord performed better than Firefox.  Where possible, I reverted to using command line for installation (apt-get and aptitude).

As for memory, try  **free -m -o**:
```
dbott@thedrake:~$ **free -m -o**
             total       used       free     shared    buffers     cached
Mem:           884        698        186          0         48        337
Swap:         3161          0       3161

```-Dave

---

### Post by kerry_s on 2007-03-16
You would do much better with a custom install with a lighter WM, something like fluxbox or icewm. A good selection of light alternative app's goes a long way to help speed. Xubuntu is growing kinda bloated and it will load stuff you might not even use.

I'm using Fluxbox, firefox and synaptic are my only heavy app's, the rest are as light as i can find because my main use is web browsing, but i can still do everything i did with a full xubuntu install. I just use lighter app's. This setup right now is my test bed for later, i want to build a silent system with no moving parts.

---

