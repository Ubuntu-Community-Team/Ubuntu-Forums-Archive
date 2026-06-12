---
title: "The infamous x205ta"
date: 2015-06-09
forum: Hardware
---

### Post by Jeremy_A. on 2015-06-09
Hello,
 I have one of the Asus x205ta laptops with xubuntu 15.04 running the rc7 4 kernel. I have icons for the battery, bluetooth, etc just from upgrading the kernel and have the grub changed to the 32bit running 64bit xubuntu. However, I do not have any windows stuff on my SDD. Idk if this is why but I don't have an nvram file in /sys/firmware/efi/efivars/. I can't complete the wifi stuff because I don't have this file.

Perhaps this is because of how I 'disabled smartboot'. As every how to on this installation doesn't tell you how to do this, but just to do it....ridiculous imho.

Anyhow, I have tried a couple of things, particularly sudo modprobe --first-time nvram, which after upgrading the OS and kernel gave back nothing.

If I reboot it is not loading nvram so I need to make this permanent. And when I manually enable it /dev/nvram is giving me read error Input/output error.

Any ideas?

Regards,

---

### Post by Bucky Ball on 2015-06-10
Welcome. Wondering what nvram has to do with your wireless. Where did you find this information? Presuming your wireless is not working and you want to get it working? Please open a terminal and copy/paste this in:

```
sudo lshw -C network
```

Post the results here between code tags (see last link in my signature). If it is a USB wireless dongle you are trying to get working, make sure it is plugged in when you are doing this. 

Please explain exactly what you are trying to do first so we can work out if nvram is actually related.

PS: Having a Windows install has nothing to do with how Ubuntu operates. You either boot into Ubuntu or Windows. They are not related or connected in a dual-boot. The only crossover would be the boot manager. Nothing to do with the actual day to day use of the install(s).

It sounds like the system is running fine apart from the fact you have no wireless ... is it?

---

### Post by Jeremy_A. on 2015-06-10
Hello,
 This is what lead me in the NVRAM direction: [https://wiki.debian.org/InstallingDebianOn/Asus/X205TA](https://wiki.debian.org/InstallingDebianOn/Asus/X205TA)

and this is the installation I followed: [https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)

Everything I am really finding about this is dated a few months.

Anyhow, what you asked for:
```

:~$ sudo lshw -C network
:~$

```

it  shows nothing. I have an external wifi card I am borrowing for the time  being since the one I bought doesn't work either.(Netgear N-300 WNA3100  v1) The borrowed wifi worked as soon as I plugged it in.

On the  PS: there a few posts on the forums here, where people talk about being  able to do the NVRAM thing on the debian link I provided to get the wifi  to at least show connections. When they did this they were using a live  cd on a flash I believe and keeping windows. Not actually nuking it and  doing a fresh install, which I have done which is why I mentioned that  windows was nuked.

From what I read NVRAM was used in both linux  and windows so I was not certain if the fact that I don't have windows  was behind why I don't have an NVRAM file.


I have the OS  running for the most part, as you can see on the links provided, there  are still issues with sound...bluetooth, perhaps the SD reader. I found  myself installing python, openssh, etc in windows which is why I just  went ahead and started this install.

I see people stating they have the wifi card working on linux kernel 4 rc3+ which is why I updated the kernel as well. At this time, I am just wanting to get the on-board wifi to function, though at this time, lspci doesn't even show the eth port, only lo.

Regards,

---

### Post by mörgæs on 2015-06-10
There is a long thread for your computer [here]("http://ubuntuforums.org/showthread.php?t=2254322"). Lots of knowledge in one place.

If you don't find a solution you could ask a moderator to merge your post into that thread.

---

### Post by Jeremy_A. on 2015-06-10
Hello,
 Yeah, I saw that post but the links to the nvram file doesn't work and everyone seems to had gotten it so other posters pointed it out and it was ignored.

Regards,

---

### Post by zetarancio on 2015-09-21
> **Jeremy_A. said:**
> Hello,
 Yeah, I saw that post but the links to the nvram file doesn't work and everyone seems to had gotten it so other posters pointed it out and it was ignored.

Regards,

Hi, I don't know if it's still relevant: you can find a fix here.
[https://wiki.debian.org/InstallingDebianOn/Asus/X205TA](https://wiki.debian.org/InstallingDebianOn/Asus/X205TA)

---

