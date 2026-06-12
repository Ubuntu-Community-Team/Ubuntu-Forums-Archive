---
title: "X-Windows Server"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by Azuka on 2006-04-26
I recently installed Ubuntu on my system. I know a little about the UNIX command line so you can be a little technical in your answer.

After installing Ubuntu, I found I couldn't run X-Windows [I'm new to Linux so please pardon me if I don't get things right]. Instead I got some garbled output and had to use the command line. The problem is obviously my monitor and video card. I have all the specifications with m. How do I configure it?

I have a book on Linux that shows me how to use Xconfigurator and xfree86 but they obviously don't come installed with it. How do I set about configuring the display?

---

### Post by lotheac on 2006-04-26
I think 'dpkg reconfigure xserver-xorg' is what you're looking for.

---

### Post by konstandinos on 2006-04-26
I'm having a similar problem.

(amd64, radeon x550)

I've done some research and everyone recommends I use the fglrx drivers. Problem is that when I try 'sudo dpkg-reconfigure xserver-xorg', the fglrx drivers are not present.

So I proceed to try install them. First I type 'sudo apt-get install linux-amd64-generic', which just confirms that my kernel is already up to date. Then I type 'sudo apt-get install xorg-driver-fglrx' but I get the error 'E: Couldn't find package xorg-driver-fglrx'.

Now I am stuck. I have tried placing the Ubuntu Live Cd in my cdrom drive, and have checked that the deb cdrom line is uncommented in /etc/apt/sources.list - but it still doesn't install (same error).

What am I supposed to do next?

I hope someone can help.

Thanks,
Konstandinos.

---

### Post by Azuka on 2006-04-26
I'm sorry -- you're being too technical. I don't really understand what you're both talking about. Could you come down to my level?

---

