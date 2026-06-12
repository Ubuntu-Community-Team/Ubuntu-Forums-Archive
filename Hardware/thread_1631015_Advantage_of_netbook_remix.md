---
title: "Advantage of netbook remix ??"
date: 2010-11-26
forum: Hardware
---

### Post by hardyfan on 2010-11-26
I am buying a netbook (Atom N455 1 gig ram 250 gig HD) is there an advantage to running the netbook remix over the full blooded OS ?  What is the remix ? what is the advantage ? What is the downside ? I run 10.04 on my Dell notebook and love it, works great out of the box.

---

### Post by mastablasta on 2010-11-26
As i understand...
Advantages:
Optimized for smaller netbook screens
Optimized for Atom processor
 
Dissadvantages:
10.10 uses unity that still needs work and to som people it gives issues.
 
note you can install normal version as well.

---

### Post by ubey on 2010-11-26
I installed 10.10 Netbook Edition on an Acer Aspire One and Unity has a few issues, as for me it slows down my computer and ruins performance.When you have installed Ubuntu, and you boot up, and the login screen appears you can actually choose between standard GUI, and the Netbook Edition. Try both, but in my opinion standard desktop-ubuntu is easier and more intuitive.

Unity is mostly just eye-candy.

---

### Post by ugm6hr on 2010-11-26
The only real difference is the user interface.
Unless you are going to use it purely for web browsing, email, skype and music, I'd suggest sticking to the standard version, particularly if you are already comfortable with it.

---

### Post by snowpine on 2010-11-26
Choose the user interface that is most comfortable for your usability needs. Check out the respective websites if you want to see screenshots of the differences, or better yet, burn Live CD/USBs of each and take them for a test drive. 

Personally I prefer the "regular" Gnome desktop on my netbook, but that is only my preference/opinion.

---

### Post by hardyfan on 2010-12-04
RESOLVED THANKS.

Thanks everyone, found your advise very helpful. The fact that everyone has the same message makes life easier.

---

### Post by rizbinetizbin on 2010-12-04
hi
I have installed ubuntu 10.10 netbook remix on my acer aspire one and  after that I had some problems in installing wine. and now every time i  wanted to edit source code or repositories it tells: “E: Type ‘b-src’ is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.”
 now I really do not no how to fix it or uninstall ubuntu because when  i tried this in terminal “$sudo apt-get remove ubuntu-netbook-remix” it  told me “E: Unable to locate package ubuntu-netbook-remix”
 so please help me doing the right thing. in one hand I need wine to  run a program in ubuntu and in other hand ubuntu’s hard way of  installing softwares made me sick.
 thanks for your help in advance

---

### Post by ugm6hr on 2010-12-05
@ rizbinetizbin:
I would suggest starting a new thread.
In that, it might be sensible to explain what you have done with your "source" and repositories.

Also - statements like "ubuntu’s hard way of installing softwares made me sick" are unhelpful, and unlikely to get a positive response from people who are sick of hearing the same complaints from new users repeatedly. As many will say, it's only hard if you expect it to be the same as what you are used to. If you stick to the Software Centre, unless you don't have an internet connection, there is nothing easier.

---

### Post by Megaptera on 2010-12-05
> **ugm6hr said:**
> @ rizbinetizbin:
I If you stick to the Software Centre, unless you don't have an internet connection, there is nothing easier.

+1 to that ... I couldn't believe how easy it was when I first started with Ubuntu, I was certain I'd missed out something important!!

---

### Post by snowpine on 2010-12-05
> **rizbinetizbin said:**
> hi
I have installed ubuntu 10.10 netbook remix on my acer aspire one and  after that I had some problems in installing wine. and now every time i  wanted to edit source code or repositories it tells: &#8220;E: Type &#8216;b-src&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.&#8221;
 now I really do not no how to fix it or uninstall ubuntu because when  i tried this in terminal &#8220;$sudo apt-get remove ubuntu-netbook-remix&#8221; it  told me &#8220;E: Unable to locate package ubuntu-netbook-remix&#8221;
 so please help me doing the right thing. in one hand I need wine to  run a program in ubuntu and in other hand ubuntu&#8217;s hard way of  installing softwares made me sick.
 thanks for your help in advance

You can install Wine with 2 clicks from the Ubuntu Software Center. I can't honestly imagine an *easier* way to install software...

Anyway, it looks for some reason like you created a file called /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list, and there is a syntax error in Line 1 of this file. I am not sure why you did this, but that is what the error message says. 

You can edit this file with:

```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
```

Look at Line 1 and fix the problem.

Or delete this file and install Wine the easy way through the Software Center.

---

