---
title: "USB live: how to restart or remember changes"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by MxM111 on 2009-01-03
Hello!
Forgive me for being complete noob, I am new to Linux, I am trying Ubuntu on my Dell XPS laptop and I decided to try it with USB install.

I have used UNnetbutin to create USB live drive. And it works. It starts and gets into desktop.

However there is no internet, not wired, not wireless. The wired and wireless options under computer icon on top right corner of the screen are grayed out. When I check drivers in the settings, some drivers are said to be disabled, because they are proprietary or something like that. According to their name they are related to wireless adapter, so I want to enable them. When I enable one shows "Downloading" and then "installing" but it stays disabled and I do not have internet connection, so I do not know how it can download anything, but another driver enabling asks for restart to enable it.

So here is a problem. As I understand I am in live session, whatever it means, so after restart I am back to exactly the same state, i.e. no changes are saved and the drivers are not enabled again. How do I fix this? Should I create new user or something? How do I boot into that user? How do I create a new user? Will it remember my changes like enabling drivers?

The important part for me is not to change the way computer behaves without Ubuntu USB, so I do not want to use hard drive for anything.

Can somebody help me? I am lost here. 
Thank you in advance.

---

### Post by MxM111 on 2009-01-04
bump

---

### Post by Just-trevor on 2009-01-04
A Live Session is when you run Ubuntu with something other than your Hard Drive, like a USB flash drive or a CD.  It doesn't effect the computer at all, and when you take the flash drive or CD out your computer is exactly the way you left it.  To save the changes, you have to install Ubuntu on your laptop, which you really shouldn't do until you are sure it will work.
First, to get internet, you need to make sure Ubuntu is seeing your wireless card - Go to Applications -> Accessories -> Terminal and type "lspci" without the quotes.  You should get a list of hardware devices like RAM Controller or Host Bridges or Sound or Graphic cards and whatever.  Look for the Ethernet Controller - It needs to be there to work
You need to install the drivers, apparently. In order to get internet, since I'm sure you're using a different computer to post on these forums, you can just plug the ethernet cable from your computer into your laptop to get internet to install the drivers, until the wireless is working, then plug it back in when you are all set.
You should get this working before you install Ubuntu onto your hard drive, in case your hardware isn't supported, or at least in my opinion.

---

### Post by Dr. GoS on 2009-01-04
I am I understanding that a live USB will act like a bigger live CD and not save the changes? Is it possible to get it to save what ever you do and use it like a bootable hard drive?

---

### Post by MxM111 on 2009-01-04
> **Dr. GoS said:**
>  Is it possible to get it to save what ever you do and use it like a bootable hard drive?
This is exactly my question. I want to find the way to use USB (which is 8GB in my case) as a bootable drive. However simply installing Linux there will kill the drive because of the constant swapping and USB stick has limited number of writes available...

So I thought USB live install could do that, but it looks that it does not remember any changes I make at all. 

Is there a solution?

---

### Post by Dr. GoS on 2009-01-14
> **MxM111 said:**
> This is exactly my question. I want to find the way to use USB (which is 8GB in my case) as a bootable drive. However simply installing Linux there will kill the drive because of the constant swapping and USB stick has limited number of writes available...

So I thought USB live install could do that, but it looks that it does not remember any changes I make at all. 

Is there a solution?

I have no expirence with this program, but my official Ubuntu flash drive does what we were describing, and does it well. I don't usually buy things, but it was for a good cause. So I guess that is always an option for you. Sorry that I cannot help you though. (This will bump the thread though!)

---

