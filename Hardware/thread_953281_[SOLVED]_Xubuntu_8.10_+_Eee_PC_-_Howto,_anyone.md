---
title: "[SOLVED] Xubuntu 8.10 + Eee PC - Howto, anyone?"
date: 2008-10-20
forum: Hardware
---

### Post by chazdraves on 2008-10-20
Greetings, all!

Well, I got one of these goofy Eee PC 900's the other day, and I'm fairly taken by it. I've been using Ubuntu Eee for the last couple days, but I'd rather run an out-of-the-box version of Ubuntu instead just for the sake of upgrading and whatnot.

I know the big issues are wifi and the hotkeys. I've found some information on how to make wifi work on the 901, but I understand the 701 and 900 use a different wireless controller than the 901/900. Can anyone post or link me to a solid guide on how to get Xubuntu 8.10 working flawlessly on Eee PC 900 hardware? I'd really appreciate it!

Thanks in advance to an excellent community!
- Chaz

---

### Post by chazdraves on 2008-10-20
Well, I'll give myself a self-serving bump and ask another question at the same time:

I just searched in synaptic for "eee" and I came up with two packages that were relavent. One was a utility that allowed you to use the functionality of the fn keys without them actually working, and another was a package that supposedly gets all of the APCI functionallity and fn keys working. I thought this sounded like a good deal, so I clicked to install it, but Synaptic tells me to do the install it would have to remove, one of which sounds awfully important to me:

apci-support
powermanagement-support
and
xubuntu-desktop

...

Any ideas? I'm guessing there's a better way to do this?

Thanks, all!
- Chaz

---

### Post by gaussian on 2008-10-20
> **chazdraves said:**
> Well, I'll give myself a self-serving bump and ask another question at the same time:

I just searched in synaptic for "eee" and I came up with two packages that were relavent. One was a utility that allowed you to use the functionality of the fn keys without them actually working, and another was a package that supposedly gets all of the APCI functionallity and fn keys working. I thought this sounded like a good deal, so I clicked to install it, but Synaptic tells me to do the install it would have to remove, one of which sounds awfully important to me:

apci-support
powermanagement-support
and
xubuntu-desktop

...

Any ideas? I'm guessing there's a better way to do this?

Thanks, all!
- Chaz

I don't own EEE yet, but just doing my homework before purchasing any netbook. But look at [http://www.array.org](http://www.array.org)

They seem to have an EEE specific kernel that solves this issue.

---

### Post by kazuo71 on 2008-10-20
Bump.

This is exactly what I was looking for :)

---

### Post by kazuo71 on 2008-10-20
> **gaussian said:**
> I don't own EEE yet, but just doing my homework before purchasing any netbook. But look at [http://www.array.org](http://www.array.org)

They seem to have an EEE specific kernel that solves this issue.

Do you have any idea if this could work on Xubuntu? It seems to be a kernel made for Ubuntu, but I don't know if that matters.

I'm actually using the kernel from [http://array.org/ubuntu/](http://array.org/ubuntu/) right now and I can confirm that it fixes the wifi on Ubuntu (8.04). The Fn keys still don't work, but that's not really important to me :P

---

### Post by gaussian on 2008-10-20
> **kazuo71 said:**
> Do you have any idea if this could work on Xubuntu? It seems to be a kernel made for Ubuntu, but I don't know if that matters.

Should not at all. Xubuntu and Kubuntu are more marketting terms for Ubuntu with different default desktop environment than "different distributions". As far as I know:

Ubuntu ==> Ubuntu minimal install + Ubuntu Desktop package 

Kubuntu ==> Ubuntu minimal install + Kubuntu Desktop package

Xubuntu ==> Ubuntu minimal install + Xubuntu Desktop package


You can make your Ubuntu be XKUbuntu (I made that name up) by doing*
```

apt-get install xubuntu-desktop kubuntu-desktop

```

*small caveat: you bootsplash picture and other minor stuff might get overwritten to the desktop you install last. It is fairly easy to undo these minor changes.

---

### Post by chazdraves on 2008-10-20
I believe that kernel is the same one that Ubuntu Eee uses. I just finished using UE, and it worked well enough, but I want a distro with proper support. The resolution and sound work perfectly in Xubuntu 8.10, the Fn keys for brightness and Suspend even work, but the wireless internet and remaining function keys are all that is missing.

Actually, switching from Ubuntu Eee to Xubuntu I noticed a huge increase in performance out of this little rig. Even Battle for Wesnoth used to stutter under Ubuntu Eee. (Mind you, I have the Eee 900 with the loley Celeron processor). Everything runs a lot better now, it's just the lack of wifi that's really getting me down.

Anywho, I've got my ears open. I don't think I want to use Adam's kernel as I'd rather stay with the official kernels - though you're right to suggest it as that is the most obvious fix for nearly everything (if it works with 8.10).

- Chaz

---

### Post by gaussian on 2008-10-20
> **chazdraves said:**
> I believe that kernel is the same one that Ubuntu Eee uses. I just finished using UE, and it worked well enough, but I want a distro with proper support. The resolution and sound work perfectly in Xubuntu 8.10, the Fn keys for brightness and Suspend even work, but the wireless internet and remaining function keys are all that is missing.

Actually, switching from Ubuntu Eee to Xubuntu I noticed a huge increase in performance out of this little rig. Even Battle for Wesnoth used to stutter under Ubuntu Eee. (Mind you, I have the Eee 900 with the loley Celeron processor). Everything runs a lot better now, it's just the lack of wifi that's really getting me down.

Anywho, I've got my ears open. I don't think I want to use Adam's kernel as I'd rather stay with the official kernels - though you're right to suggest it as that is the most obvious fix for nearly everything (if it works with 8.10).

- Chaz

It is my understanding that you have two options at the moment to get the wireless working:

1) Use Adam's kernels. I think they are only for 8.04 at the moment
2) Build the kernel-modules needed to get the wireless working yourself.

I can certainly see why someone would prefer 2, but it requires even more technical sophistication than 1 (although not by much).

---

### Post by kazuo71 on 2008-10-20
> **gaussian said:**
> Should not at all. Xubuntu and Kubuntu are more marketting terms for Ubuntu with different default desktop environment than "different distributions". As far as I know:

Ubuntu ==> Ubuntu minimal install + Ubuntu Desktop package 

Kubuntu ==> Ubuntu minimal install + Kubuntu Desktop package

Xubuntu ==> Ubuntu minimal install + Xubuntu Desktop package


You can make your Ubuntu be XKUbuntu (I made that name up) by doing*
```

apt-get install xubuntu-desktop kubuntu-desktop

```

*small caveat: you bootsplash picture and other minor stuff might get overwritten to the desktop you install last. It is fairly easy to undo these minor changes.

Yeah, that's what i hoped. Thanks for clearing it up ;).

---

### Post by amp711 on 2008-10-20
I don't have the 900 you own, but I have a 1000HD w/ the Celeron 900 in it.  Bumped the ram to 2Gb and plan on putting bigger/faster hard drive in it soon.

I installed 8.10 when I bought the machine and it has been working flawlessly.  Literally no issues.  Fairly fast and it appears that the bottleneck is mainly the processor when I start pushing it.  

When the dual core Atoms are out, I will likely upgrade... but in the interim I am impressed with 8.10 and the 1000HD..

---

### Post by gaussian on 2008-10-20
> **amp711 said:**
> I don't have the 900 you own, but I have a 1000HD w/ the Celeron 900 in it.  Bumped the ram to 2Gb and plan on putting bigger/faster hard drive in it soon.

I installed 8.10 when I bought the machine and it has been working flawlessly.  Literally no issues.  Fairly fast and it appears that the bottleneck is mainly the processor when I start pushing it.  

When the dual core Atoms are out, I will likely upgrade... but in the interim I am impressed with 8.10 and the 1000HD..

Since I am thinking of purchasing one (or Dell Mini or something else): does wireless work with 1000HD with Ubuntu 8.10 out of the box? (Sorry about the thread hijack)

---

### Post by chazdraves on 2008-10-20
Well, I guess I'll answer my own question:

[http://www.corey-m.com/blog/?p=309](http://www.corey-m.com/blog/?p=309)

That seems to do the trick quite well. It seems to a be a fairly well-known workaround, so I doubt I'm educating anyone, but this really does work as I'm using the wifi right now.

I didn't try the tricks for the Fn keys yet (mostly cause that's not a big deal for me.

Thanks, all
- Chaz

---

### Post by bhaverkamp on 2008-10-31
thanks, that fixed things for me on my 1000 HD!

---

### Post by ljonesj on 2008-11-01
well in 8.04.1 adams repo is added for the eee kernal and its added to 8.10

---

