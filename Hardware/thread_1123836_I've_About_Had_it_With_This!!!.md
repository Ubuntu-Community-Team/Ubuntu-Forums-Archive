---
title: "I've About Had it With This!!!"
date: 2009-04-12
forum: Hardware
---

### Post by chessnerd on 2009-04-12
(I apologize for the long post, but I want to provide all of the details I can. The short version is: Do you know how to make a Dynex DX-SC51 sound card work with Xubuntu?)

I purchased a Dynex DX-SC51 sound card for my desktop that is running Xubuntu. The internal sound card does not work, although apparently it does have one, and I wanted to listen to music on this computer. I posted on this forum a while ago about my problem and didn't get any response, but I tried to figure out the solution on my own anyway.

I looked everywhere I could online, I looked in two books about Linux (The Official Ubuntu Book and Linux for Dummies), and I messed around with sound options for what feels like hours. I cannot find out how to get the stupid card to work. ](*,)

Yesterday, I updated to Xubuntu 8.10 and, for whatever reason, the card worked. I was ecstatic and quickly posted a "nevermind" in the other thread that I had started, thinking I would never have to deal with the problem again. However, I booted up the computer today and tried to listen to music only to find that the card doesn't work again. :mad:

I've about had it with this stupid process. Never have I had a problem with Windows like I've had with Linux. I like Xubuntu and I like Linux, but unless I can use it without these kinds of issues I might have to just run fdisk /mbr and be done with Linux.

I haven't given up yet and I'm willing to provide any details necessary and even work with the code for Xubuntu to get this card to function properly. I really want Linux to work for me. I want to use an open source operating system that doesn't restrict it's users like Windows and OS X does, but unless I can USE it, that isn't an option.

Here's what I've done so far:

1. I put the card in a working PCI slot and booted into Windows 2000, installed the drivers from the CD, and the card worked.
2. I booted into Xubuntu 8.04 and it detected the card, but no sound would come out from any of the ports even after making it the card used under Applications>Settings>Settings Manager>Sound.
3. I looked around online to find a solution, but instead only found a bunch of people saying how Ubuntu was able to instantly pick up and use the card, not helpful.
4. I read the "Linux for Dummies" sections about sound cards and found out about alsamixer. After running that, I found that alsamixer was using the integrated Intel card which does not work.
5. I read "The Official Ubuntu Book" and tried the suggested command to load the module into the kernel:
```
sudo modprobe snd-ice1724
```
No errors came up. I loaded alsamixer and the Intel card was still the one it was working with.
6. I upgraded to 8.10 yesterday and, magically, the card worked.
7. I booted the computer today and the card is no longer working.

Please help me with this...

---

### Post by prahs rozar on 2009-04-12
I think it could be a problem with PulseAudio. It was introduced in either 8.04 or 8.10, but as soon as I upgraded to 8.10 I had no sound. I forget exactly how I fixed it, but you may be able to find some information on it if you search. I do remember it was a real pain though.

---

### Post by chessnerd on 2009-04-13
Prahs, thanks for your reply. From what I've read, Xubuntu doesn't come with pulseaudio fully installed, only with one related package (I'm guessing you were thinking for Ubuntu). I don't think uninstalling it will having any positive effects, but I'm glad that someone was willing to put in a bit of time to work towards a solution to my problem.

Anyway, I talked to a couple of guys I know who use Linux and one of them was able to give me a solution that seems to have worked for real this time (even after a reboot). He told me to go into BIOS and disable the defective card so alsamixer would have to use the Dynex one by default. That looks like it did that trick. The card is working even after reboot.

I really hope I don't have to make any more posts about this, and I don't think I will this time.

---

