---
title: "Getting sound working on a toughbook CF-71"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by aveline on 2005-07-29
I posted about this once before &  got no answers however since then I found a webpage about how to do this.  Problem is I don't understand the instructions entirely & wondered if someone could put them into more plain english for me & others with this type of laptop.

[http://www.blackbeauty.de/members/ergo.html](http://www.blackbeauty.de/members/ergo.html)

thats the best I've found so far.  I set the sc's address & irq's to defaults in the bios where it says these are SB-like (compatible?) settings that can be enabled and changed as needed.  But ubuntu doesn't even detect the card.  lspci doesn't list anything and all sound tests tell me no device found.  So I'm open to ideas.

aveline

---

### Post by aveline on 2005-07-30
[QUOTE=aveline]I posted about this once before &  got no answers however since then I found a webpage about how to do this.  Problem is I don't understand the instructions entirely & wondered if someone could put them into more plain english for me & others with this type of laptop.

[http://www.blackbeauty.de/members/ergo.html](http://www.blackbeauty.de/members/ergo.html)

thats the best I've found so far.  I set the sc's address & irq's to defaults in the bios where it says these are SB-like (compatible?) settings that can be enabled and changed as needed.  But ubuntu doesn't even detect the card.  lspci doesn't list anything and all sound tests tell me no device found.  So I'm open to ideas.

aveline[/QUOTE]
 anyone??

---

### Post by aveline on 2005-08-13
[QUOTE=aveline]anyone??[/QUOTE]
 well I'm gonna ask this here instead of starting a new thread.  On Mepis iirc I was able to run "alsaconf" & it found and setup my soundcard perfectly.  I tried running alsaconf on ubuntu but it says file not found?  how can I get alsaconf installed properly to do this & test it to see if it will work on ubuntu?  

I also followed the unofficial guides setup sound properly thing & somehow that fixed one problem.  It seems that before using the guide, if i did lspci -v, it did show my sound card as a YMF744 (i think) but all the irqs and dma slots were "unvailable".  After using the guide it shows at least one irq & 1 dma slot correctly used, but the 2nd dma & irq slots are unavailable.

I found some sites that detail things to do w/this quirky little onboard soundcard, and were this not a laptop I'd just stick another sound card in this thing + the fact I know it works on linux just not ubuntu atm.

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Yamaha&card=Waveforce+192+Digital.&chip=YMF724%2C+YMF740%2C+YMF744%2C+YMF754&module=ymfpci](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Yamaha&card=Waveforce+192+Digital.&chip=YMF724%2C+YMF740%2C+YMF744%2C+YMF754&module=ymfpci)

Tried using modprobe to insert the module that page suggests & it does so w/out complaint.  But still no sound and I'm not sure I need to compile alsa & all the other stuff that page suggests...

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)  used some of that page to help a bit but I couldn't follow all the directions heh.

Anyway if anyone knows how to get alsaconf to work on ubuntu I'd be grateful.  I'm just detailing what progress I've made so far both for My own reference and any one else who cares.

---

### Post by s_p_a_r_k_y on 2005-08-13
its in the package alsa-utils

```
 sudo apt-get install alsa-utils 
```

although I'm pretty sure it should have been installed with ubuntu. Try 
```
 locate alsaconf 
```
to find any references to it

---

### Post by aveline on 2005-08-14
[QUOTE=s_p_a_r_k_y]its in the package alsa-utils

```
 sudo apt-get install alsa-utils 
```

although I'm pretty sure it should have been installed with ubuntu. Try 
```
 locate alsaconf 
```
to find any references to it[/QUOTE]
 tried to do a slocate alsaconf & i find nothing either doing it as a user or doing it with sudo in front of slocate first.  alsa-utils *is* installed though....

soooooo what gives???  :confused:

---

