---
title: "Is it possible to get tty's simliar to that of gentoo?"
date: 2008-10-15
forum: General Help
---

### Post by jerome1232 on 2008-10-15
Mostly I'm talking about the stuffed penguin in the top left, and how '[ok]' and '*' is colored. I know how to get a nicely colored bash prompt and change the resolution of the tty's.

I would like to turn off my usplash and have a text logon but I still want it to look nice :)

see screenshot for an example, it's a freshly booted live cd.

---

### Post by hyper_ch on 2008-10-15
have a look at your ~/.bashrc and and enable the fanzy color thing... you'll see, there's one color option commented out ;)

---

### Post by jerome1232 on 2008-10-15
Yeah that changes the prompt though, which I already have customized to show things useful to me and give it a little color. It also is only capable of changing all text. 

I'm thinking bashish might be able to do more of what I want, so I'll take a look at that.


I was hoping to... I guess use the framebuffer to render an image like what gentoo does in my screenshot.

---

### Post by xENO_ on 2008-10-15
Gentoo uses a kernel with different compile-time options (and patches) than Ubuntu.  If you built your own kernel image you could have that penguin logo in the corner, or, if you wanted something more elaborate (also from Gentoo) you could apply the gensplash patches and use some trickery to get the userspace pieces of it into the initramfs, then you could have a high resolution, fully themed tty.

---

### Post by jerome1232 on 2008-10-15
I was afraid it would involve Kernel recompiling. I'll have a go at getting it to work in a VM and then think about it for my machine :)

I have a high res, custom prompt tty now and I'm happy with it for now. If you have suggestions as to what I need to change in the kernel and/or utilities that would make it easier it would be much appreciated.

I've only compiled a kernel while following the gentoo handbook during a gentoo install before so I'm new at this aspect. That gentoo handbook has alot of little gems of knowledge in it! 
(Like I didn't know there was a 15 partition limit in each extended partition)

---

### Post by Sam on 2008-10-15
To colorize the [ok] in green:
```
gksudo gedit /etc/lsb-base-logging.sh
```
Search for
```
log_end_msg () {
```
in this function you'll find
```
            echo "[ OK ]"
```
Replace with:
```
            printf '[ '
            $TPUT setaf 2 # green
            printf ok
            $TPUT op # normal
            echo ' ]'
```
Save and exit.

To remove the splash screen and boot in text mode:
```
gksudo gedit /boot/grub/menu.lst
```
Search for:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash quiet
```
Replace with:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet
```
Then:
```
sudo update-grub
```

---

### Post by jerome1232 on 2008-10-15
Great tip! Looking over a couple things I noticed in /lib/lsb/init-functions It seems to have alot of functions already defined that check for use_fancy_output and it will do more colorizing? (like red fail messages and such)

I also found some patches for debian to get more fancyiness.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=416485](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=416485)

I just don't get how to set the 'use_fancy_output' flag so it will start doing that stuff!  (btw your patch worked, after looking at various things I was just thinking this other script is where you are supposed to set such things)

---

### Post by Sam on 2008-10-15
Also, to colorize the prompt:

Add at the end of ~/.bashrc and /root/.bashrc (open this file with sudo)
```
if [ $UID -eq 0 ] ; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[00;31m\]\u@\h:\w#\[\033[00m\] '   
else
    PS1='${debian_chroot:+($debian_chroot)}\[\033[00;32m\]\u@\h:\w$\[\033[00m\] '
fi
```
This will make the prompt green and in the case of your logged with root (e.g. using "sudo su") it will be red.

---

### Post by RedSquirrel on 2008-10-15
Under # defoptions in /boot/grub/menu.lst, I like to remove the "quiet" as well. Let's see all the gory details! :)

---

