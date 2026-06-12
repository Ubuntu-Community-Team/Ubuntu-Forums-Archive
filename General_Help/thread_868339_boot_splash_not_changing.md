---
title: "boot splash not changing"
date: 2008-07-23
forum: General Help
---

### Post by jimi_hendrix on 2008-07-23
hi all

so ive got this shiney silver theme going for my computer and found i can change my boot splash to match this from the ubuntu logo

so i go to system > preference > splash screen and picked my cool silver dragon thing that i installed

i enabled "show splash screen on start up"

and clicked activate

yet when i start up ubuntu i still see the ubuntu logo and loading screen while it loads

if i am wrong about what a splash screen is please tell me

i also have the same picture as my log in screen if that means anything

---

### Post by jombeewoof on 2008-07-23
> **jimi_hendrix said:**
> hi all

so ive got this shiney silver theme going for my computer and found i can change my boot splash to match this from the ubuntu logo

so i go to system > preference > splash screen and picked my cool silver dragon thing that i installed

i enabled "show splash screen on start up"

and clicked activate

yet when i start up ubuntu i still see the ubuntu logo and loading screen while it loads

if i am wrong about what a splash screen is please tell me

i also have the same picture as my log in screen if that means anything
Several different splash screens are involved.

Grub can have a splash screen
usplash is what hides all the "funky OS gibberish" and gives you the initial loading screen

You are then presented with a login screen (gdm or kdm) which can be themed

then you have the splash screen

which one are you trying to change?

---

### Post by jimi_hendrix on 2008-07-23
i alrdy got the login one to have my dragon and i like my grub in the DOS-esq style thats the default (so when someone noses into my laptop there greeted with a confusing DOS screen which might scare them) so that leave the one that hides the "funky OS gibberish"

and heres the dragon i want to change it to for the curious

---

### Post by jombeewoof on 2008-07-23
alright dude, I did a whole bunch of research on this most pain in the butt of a subject. 

install splayshy, it's in the repo's you can get it from synaptic.

make sure to edit /boot/grub/menu.lst 

you will need to add vga=791 to the end of your kernel line for whatever kernels you boot.

Then you just have to mess with themeing it.

---

### Post by jimi_hendrix on 2008-07-24
couldnt find find it in synaptic i have no clue what you mean by editing boot/grub/menu or where to add vga=791 so i guess ill settle witht he ubuntu logo :) unless you rly want to take time from your day to explain all that

i am sry that you wasted all your time on that research

ty anyway

---

### Post by jombeewoof on 2008-07-24
No sweat man, I've been trying to figure this out for a while.

It's probably in a repo you don't have enabled. 

Here is my sources.list 
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ hardy partner
# deb-src http://archive.canonical.com/ubuntu/ hardy partner
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://security.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://security.ubuntu.com/ubuntu/ hardy-security universe
deb http://security.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu/ hardy-security multiverse

```
What do I have that you don't
As far as editing the kernel entry
look at /boot/grub/menu.lst down toward the bottom you'll see 
```
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=8bdad6bd-0868-42d1-a1e7-4f1b15dc762d ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

```
Change the kernel line to 
```
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=8bdad6bd-0868-42d1-a1e7-4f1b15dc762d ro quiet vga=791 splash
```

The only issue I've found is the app doesn't want to let me change the bootup screen, I can easily change the shutdown splash to whatever I want but it defaults to an image that doesn't even exist for bootup if I change the theme from default.

It probably has something to do with my images.

---

### Post by jimi_hendrix on 2008-07-24
ok 2 questions

1. i cant find splayshy in synaptic
2. weres the file with the kernel line

---

### Post by jombeewoof on 2008-07-24
> **jimi_hendrix said:**
> ok 2 questions

1. i cant find splayshy in synaptic
2. weres the file with the kernel line

I apologize, it's splashy, not splayshy.


1. run the following commands
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
```
```
gksudo gedit /etc/apt/sources.list
```
The paste my file into the now empty file that gedit pulls up.
then run 
```
sudo apt-get update && sudo apt-get install splashy
```

2.
Then you will want to run 
```
gksudo gedit /boot/grub/menu.lst
```
Find the line toward the bottom that says kernel (there may be several of them) and add the vga=791 just before the splash argument.
and make the changes I posted in my last post.

This file is very important to the startup of your PC, so don't mess it up.

---

### Post by jimi_hendrix on 2008-07-24
did that now what?

---

### Post by jombeewoof on 2008-07-24
now you need to set the splashy splash screen.

```
sudo splashy_config --help
```
will tell you what you need to know.

-i installs new themes. 
If you install the theme pack, they are installed in /etc/splashy/themes/

So to install a theme called waterfire.tar.gz I would 
```
sudo splashy_config -i /home/tom/waterfire.tar.gz
```
-s sets the theme so
```
splashy_config -s waterfire
```
would turn that on

---

### Post by Lakjin on 2008-07-25
i had a similar problem. i kept trying to get the fingerprint splash screen to show up but it just wouldnt. i did everything that their directions said.

in the end, i did get it to work and this is how:
(you need startup manager for this. if you dont have it, sudo apt-get install startupmanager)

Go to System -> Administration -> Start-up Manager
Under display change the resolution. I changed mine to 1074x768 and that made it work. You can try that and if it doesnt work try a different resolution.

There should be no need to change from usplash to splashy or w/e, but if you want to go that path, you are more then welcome to.

---

### Post by jimi_hendrix on 2008-07-25
ok 2 things

1. i installed start up manager changed the resolution now how do i set the picture i want

2. after i installed splashy i restarted my computer and saw a pic of tux as the start up thing not wanting this and prefering the good old ubuntu one until i figured this out i undid the vga=791

now i get verbose mode what do i do?

---

### Post by Lakjin on 2008-07-25
TBH i have no used splashy so I dont know.

if you were using usplash i could tell you how to change it back to ubuntu...

try looking under startupmanager. under appearance it says "usplash themes" at the bottom...maybe it will have a "splashy themes"?

---

### Post by jimi_hendrix on 2008-07-25
how do i switch back to usplash...splashy is just confusing me

---

