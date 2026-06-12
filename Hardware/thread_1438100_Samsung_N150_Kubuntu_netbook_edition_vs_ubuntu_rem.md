---
title: "Samsung N150: Kubuntu netbook edition vs ubuntu remix"
date: 2010-03-24
forum: Hardware
---

### Post by LK_gandalf_ on 2010-03-24
Hi all, I'll soon have a samsung N150, and I want to install linux. I use Kubuntu on my laptop, so I thought to try kubuntu also on the netbook. I've read on the kubuntu webpage that the netbook edition is still a not fully developed version, so I was wondering if it will be a good choice.

Anyway, what are your experiences with a Samsung N150 and Ubuntu or Kubuntu?
Thank you ;)
I hope this topic can be useful and collect all the informations for all the people who want linux on this netbook.

---

### Post by LK_gandalf_ on 2010-03-29
any idea?

---

### Post by jbun on 2010-04-08
Hi

I have been using UNR /UNE since 9.04 on an Medion e1219 (like MSI wind - 1.6 atom / 1gb ram etc). I am currently running the update to date version of Lucid Alpha 3. I enjoy the following;

- Good looking GUI and easy / fast access to applications
- easy connection to net (3g or wireless)
- good battery life
- snappy boot ups and resumes.

I do sometimes find the full screen function is a little funny for some applications, but none of the ones bundled by default with the live CD cause we any grief.

I have also tried Kubuntu (the demo version via USB and alpha 3 on the hard drive). I liked the look, but personally, I found it harder to use and frustrating when connecting to networks (to this day I have not been able to connect via a 3g modem). It is also slower when launching apps or flicking between menu options. 
I found basic tasks much more difficult to do (see this thread for an example [http://ubuntuforums.org/showthread.php?t=1343176](http://ubuntuforums.org/showthread.php?t=1343176) ). However, if you already use Kubuntu you may have a head start in this regards. 

So for me its Ubuntu Netbook edition over Kubutu NE.

---

### Post by JC Cheloven on 2010-04-24
To the OP:
I've just had in my hands the N150 this evening. Know what?
[SIZE="5"][COLOR="Blue"] there is no boot option in the bios !!!!!!!!!!!!!![/COLOR][/SIZE]

So I was unable to try out ubuntu. In fact there is no possibility (well, I don't figure out) of installing any OS other than windoze. 

I'm still schocked :confused:
JC
_____________

---

### Post by sevenflo on 2010-05-04
Okay let's not get too crazy there. There is a boot option. I'm running Ubuntu Netbook Remix on an N150 right now.

The only issue I have on it though, is brightness can only be adjusted at the GRUB screen or using the setpci command in the terminal. Wish I had known this earlier.

Secondly, my wifi cuts out when I 'overwhelm' the system a bit. Overwhelmed being having a few downloads at once. Though not everyone has this issue with the N150. 

Good luck!

---

### Post by bryleed on 2010-05-11
Dumb question: what GRUB or 'setpci' options do you refer to for adjusting screen brightness?

I'm a Ubuntu novice, so please explain delicately.  Thanks.

---

### Post by sevenflo on 2010-05-15
> **bryleed said:**
> Dumb question: what GRUB or 'setpci' options do you refer to for adjusting screen brightness?

I'm a Ubuntu novice, so please explain delicately.  Thanks.

Hi Bryleed, 

GRUB is a screen that comes up before your operating system (Windows or Linux) loads up. If you don't have Windows installed, (only Linux), you may not see the grub screen at all - that is, unless you press F8 or F10 (not sure what the key combination is, but you can search for that). Your goal is to see a screen that has a list of items that look like 'Ubuntu 10.04, Kernel 2.6.21...' and so on (your numbers may vary).

At that screen, press the up or down key once to remove the timer (otherwise the system will choose a selection within 10 seconds). NOW, try your brightness keys. Your screen should brighten or dim as you wish - but choose wisely, because you'll have to restart to change the brightness using this method. 

Option 2, supposedly will allow you to alter your brightness within the Ubuntu. Go to Applications -> Accessories -> Terminal (depending on the system you're using, Accessories might be System Tools).

Once the terminal is open, you would type something like this in:

```
setpci -s 00:02.0 F4.B=66 (a value between 00 and FF, where FF is 100%)
```

Problem is, I don't know what that means and haven't tried it yet.

The source for that and the original author is at: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/397617](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/397617)

and

[http://ubuntuforums.org/showthread.php?t=1031764&highlight=setpci+samsung](http://ubuntuforums.org/showthread.php?t=1031764&highlight=setpci+samsung)

Wish I could help you out there but I don't have the netbook around at the moment. Let me know if you need any clarification! 
Note, I will be away until Tuesday.

---

### Post by humbug01 on 2010-05-23
I'm waiting for my Samsung NB30 now and found this site with tools for screen brightness and nice forum in case you haven't seen it yet:

[http://www.voria.org/forum/viewforum.php?f=15]("http://www.voria.org/forum/viewforum.php?f=15")

It might be of help.

---

### Post by Thomas Humphrey on 2010-06-05
Probably a little bit late, but I've just put Ubuntu 10.04 on my N150. Since updating seems to work fine, however can't connect on wifi as of yet.

---

### Post by muleyyy on 2010-06-14
Hi Just to let you know, i just put ubuntu netbook edition on my N150....

everything works out of the box except for the wireless, but that was simple enough to fix, if you google around you will find the fix, aparrently its a firmware problem.
[edit] here is the actual commands i had to put into the terminal to fix it;
[B][FONT=Arial][SIZE=2]
[COLOR=SeaGreen]sudo apt-get install git-core
cd /tmp
git clone git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/firmware.git
sudo cp -av firmware/RTL8192E /lib/firmware/[/COLOR][/SIZE][/FONT][/B]

the webcam is a little slow starting up though, and bluetooth is always enabled on startup but apart from that it runs really nicely and i'm quite pleased with it, much better than the bloaty half o/s (win7 starter ed) that came with it.

---

### Post by muleyyy on 2010-06-21
Hi I'd like to add some comments, having been using netbook edition on my n150 for a few days now. 

The only remaining niggle is the wireless switches itself off and behaves very peculiarly when the system hibernates, it doesnt cause me any major headaches but i think i will have to investigate as time goes on

things i have tested since my last post though...

-Webcam works, but is a little slow, if you go into preferences, and close it without making any changes it suddenly seems to enable itself and work fine.

-Card reader was very fast at transfering files


also the brightness thing only working in grub appears to be common to all ubuntu derived linuxes, i tried it with mint and the brightness could be adjusted while the system was deciding what o/s to boot in, but as soon as you try to boot it in linux you cant control the brightness

---

### Post by Farg22 on 2010-08-13
> **JC Cheloven said:**
> To the OP:
I've just had in my hands the N150 this evening. Know what?
[SIZE="5"][COLOR="Blue"] there is no boot option in the bios !!!!!!!!!!!!!![/COLOR][/SIZE]

So I was unable to try out ubuntu. In fact there is no possibility (well, I don't figure out) of installing any OS other than windoze. 

I'm still schocked :confused:
JC
_____________

One can, first of all, you must create a pen drive with iso image of ubuntu to install, connect, restart the pc, press f2 you enter the bios, go to boot, change the usb mode in the first line (should appear entering the first line, you know the brand of your flash drive) with the x you leave it on the number, f10 and should start, I do like that, but it achieves cost, I hope you will serve, as writing apology use a translator.

---

### Post by Farg22 on 2010-08-13
I need help, I installed ubuntu 9.04 desktop edition on my netbook samsung N 150, works perfect, except it does not recognize the FN key referring to the light, screen and almost all blue, except for audio, I tried with several codecs no use to me , Also to go online in face appears too large, apparently does not recognize either the monitor, said the unknown, I have tried to improve and it is not, if anyone knows how to do it even if it was from the terminal, would appreciate the help. I used the translator unless you understand mucho.disculpen. Thank you.

---

