---
title: "Beryl kernel 2.6.17-10-generic"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by rossjman1 on 2006-11-20
First of all let me just say that I'm ecstatic that I got Beryl working, and that Ubuntu Edgy detected everything on my laptop (except for the fingerprint reader) - something I cannot say about Vanilla Debian Testing and Knoppix. I have an IBM (Lenovo) ThinkPad T60 with Intel Core Duo. I'm told that I need to boot with kernel 2.6.17-10-generic to utilize booth cores, and I can see that this is true when I run 'top'. There's a couple things that are stopping me from using this kernel versus kernel 2.6.17-10-386.
1) When booting the generic kernel boot time is increased
2) Beryl doesn't work when using the generic kernel (the window decorations flicker on and off rendering them useless and unpleasing to the eye)
So, my question is is this a normal occurrence or do I just have bad luck? Is there any way that I can use my existing Beryl installation and configuration and use my dual core processor to its full potential? Thanks in advance.

If you need them here are more specs:
Intel Core Duo 1.83GH
1GB RAM
ATI Mobility Radeon X1400 512MB - I'm using the right drivers as specified by the Beryl installation instructions.

---

### Post by rossjman1 on 2006-11-21
bump

---

### Post by didobuntu on 2006-11-21
Hello,

Beryl should work perfectly with this kernel. I have an Asus laptop with Core Duo T2500 and an ATI Mobility X1600 card. All should run well.

---

### Post by compmodder26 on 2006-11-22
I too have a T60 running the generic kernel and beryl is running smooth as silk.

---

### Post by bob_c_b on 2006-11-23
Beryl hangs on my T60 as well, works fine during a session but if I log out or restart GDM crashes. Works perfectly without Beryl installed.

---

