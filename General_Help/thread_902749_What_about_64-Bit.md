---
title: "What about 64-Bit?"
date: 2008-08-27
forum: General Help
---

### Post by tmcw33 on 2008-08-27
What's the likelihood of creating a 64-bit version of Wubi?

---

### Post by gnuvistawouldbecool on 2008-08-27
If your computer is 64 bit, then Wubi will download the 64 bit version of Ubuntu.

Wubi itself is pretty much a downloader, and doesn't really need to do anything else other than that, so it doesn't need to be 64 bit itself.

---

### Post by Crafty Kisses on 2008-08-28
It will install the  64bit. To make sure you can go to System Monitor and see if both of your cores are working.

---

### Post by tmcw33 on 2008-08-28
I have WinXP 32-bit, but I also have a 64-bit processor AMD64 4000+. Wubi only downloads the 32-bit version, which is the reason I was asking. It would be nice if there was an option to download the 64-bit when Wubi only detects 32-bit.

---

### Post by tmcw33 on 2008-08-29
No answer in 21hrs, so I'm guessing there's no solution? :confused:

---

### Post by phearsome on 2008-08-29
I believe it might be possible to install it with a --64bit argument. It is possible to force installation of 32bit, so it might work. Otherwise you could place a 64bit iso file in the same folder as the Wubi installer, I think.

I am not entirely sure, though.

---

### Post by tmcw33 on 2008-08-29
I'll have to give that a try when I get home.

---

### Post by Crafty Kisses on 2008-08-29
I'm pretty sure you have 64-bit have you checked?

---

### Post by tmcw33 on 2008-08-31
> **Codename said:**
> I'm pretty sure you have 64-bit have you checked?

Being new to Ubuntu, I'm not sure how to check the version. I can tell you that Ubuntu only sees 2.5 of my 4gb of memory like Windows.

---

### Post by ke9v on 2008-08-31
> **gnuvistawouldbecool said:**
> If your computer is 64 bit, then Wubi will download the 64 bit version of Ubuntu.

Wubi itself is pretty much a downloader, and doesn't really need to do anything else other than that, so it doesn't need to be 64 bit itself.

I found that out today. I have a Vista box gathering dust so, having never played with Wubi before I thought I'd give it a go and see how it works.

The execution was flawless and all is fine so far as I can tell -- but there was not an option for 32 or 64 bit Hardy in Wubi -- and as I have since come to learn, I now have 64-bit Hardy running on this box...

Jeff

---

### Post by tmcw33 on 2008-08-31
Does this mean I'm on 64-bit?

2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

If I am, why does only 2.5gb of memory show? I thought 64-bit would show all 4gb.

---

### Post by tmcw33 on 2008-09-03
I guess the answer is unknown?

---

### Post by ke9v on 2008-09-03
FWIW, I did have a closer look at the FAQ for Wubi and found that you can get the 32-bit OS even if you are running a 64-bit machine by using the command line switch "--32bit".

I deleted the 64-bit install and used the --32bit command and as expected, got the 32-bit OS and all worked flawlessly.

---

### Post by tmcw33 on 2008-09-04
> **ke9v said:**
> FWIW, I did have a closer look at the FAQ for Wubi and found that you can get the 32-bit OS even if you are running a 64-bit machine by using the command line switch "--32bit".

I deleted the 64-bit install and used the --32bit command and as expected, got the 32-bit OS and all worked flawlessly.

Not trying to be rude, but that has nothing to do with my question. I want 64-bit but I want to know why it's not seeing my entire 4gb Ram.

---

