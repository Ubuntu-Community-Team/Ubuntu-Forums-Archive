---
title: "Roaming Ubuntu - boot questions"
date: 2008-04-22
forum: Hardware
---

### Post by Huss on 2008-04-22
Hi all

I have had ubuntu installed on my external HD for 6 months now and have always wanted to be able to be able to boot on other hardware configs. I've started to experiment on a few computers and have had a few victories. Today, I disabled my Nvidia driver and plugged my HD into another computer. It loaded to GRUB and went through the boot-up process and then (after the progress bar reached 100%) there was a blank screen. I played around until I got a command line instead of that blank screen then ran out of ideas. 

Why am I getting this error, will I get it with every different configuration, and how do I fix it with min risk to my system? 

If I ran sudo dpkg-reconfigure xserver-xorg and then startx would that do the trick?
So many questions.

Help and explanations would be appreciated.


Release: Gutsy

---

### Post by Huss on 2008-04-24
I got it!

It took a bit of messing around but it was worth it. Now I don't need to take my laptop to work - only my external HD. 

The basic steps in getting it working were:


1) back-up a working configuration of the x-org file. You can find it here: /etc/X11/xorg.conf

*If you make a mistake and can't boot to your normal system you may have to replace your xorg.conf file ... I did. To revert back to a back-up I coded in the boot command line:
sudo su
cp /home/[where you put your back-up]/xorg.conf /etc/X11/
Then: startx
(it might be best to reboot instead of going into the GUI. If you code startx then you will be logged in as root - everyone seems to say that it's not a good idea)

If you cant get to the boot command line look at step three

2) Set USB boot priority in the bios. 

3) If grub loads up (and the boot hangs at the end of the progress bar) then press 'e' on your Ubuntu boot entry and then edit the Kernel line. Mine changed from this:
/boot/vmlinuz-2.6.22-14-generic root=UUID=7afb27a6-6dfd-4513-b7ce-2a312eaf7519 ro verbose splash vga=792

To this:
/boot/vmlinuz-2.6.22-14-generic root=UUID=7afb27a6-6dfd-4513-b7ce-2a312eaf7519 ro verbose

When I booted this way I was given the chance to enter my username and password at the command line.

4) after entering the UN and PW, I ran: 
sudo dpkg-reconfigure xserver-xorg 

and wrote down the driver - intel
the video card, and the pci, which for me was :0:2:0

Because reconfigure xserver-xorg wouldn't write to my xorg file I booted up to my configured laptop 

5) Then go through the screens and graphics section and double check the driver and screen names

6) Editing my xorg.conf: I replaced all references to my normal driver, pci and monitor with the new ones and then rebooted 

--> I will post the two different config files if anyone needs.

I got it to work after the second revision of the xorg.conf file. 
 

I know it's a long process but it's great to be able to roam with an external HD. I hope a group of Ubu-gurus will be able to run with this and make roaming a standard feature. It seems like the monitor settings and graphics drivers are the main thing in the way. Don't make me do this to every new config I use!


P.S. When in the non-gui command prompt: 
- Can I edit files (like xorg.conf)? if yes, how?
- What's the command for rename?
- Another noob one: how do I list (ls) or use a help function and see the whole lot? Dos used dir/w or dir -p, what do we use?

P.S.2. Does Hardy fix this?

---

### Post by mick8985 on 2008-04-25
Hi Huss, glad to see you got this working, In answer to your questions.
The easiest console text editor is nano
```
sudo nano /etc/X11/xorg.conf
```
When you think about it, renaming is the same as moving, so there is no need to write 2 commands to do the same function.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.1
```
In linux there is another command which does the /p function, its called more, this will take the output of any command and show it page by page, to join these commands together we use | (pipe)
```
ls -l | more
```
and the new version of xorg used in hardy should be able to configure itself on the fly, so it should go a long way to making this easier, but from what I have seen so far it perhaps still needs some work before its perfect. You should give it a go and report how well it works.

---

### Post by Huss on 2008-04-25
Thanks again, they may come in handy.

I'll switch to hardy in a few weeks.

---

