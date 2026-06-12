---
title: "ATI Radeon HD 3200 Display Driver problems."
date: 2011-02-15
forum: Hardware
---

### Post by Donzieja on 2011-02-15
Hello, all. Please excuse any significant lack of detail in this post. You may or may not have noticed that I have a habit of posting things right after I wake up at 4:00 in the morning. ANYWAYS! On to the problem... I need this:

[http://archive.debian.org/debian/pool/main/e/eglibc/libc6-dev_2.11.1-0ubuntu7.2_amd64.deb](http://archive.debian.org/debian/pool/main/e/eglibc/libc6-dev_2.11.1-0ubuntu7.2_amd64.deb)

And it isn't there. 

Does anyone have it?

Thanks,

-Don

P.s - You're more than welcome to request more detail.

EDIT: It seems I've (yet again) located it:

[https://launchpad.net/ubuntu/lucid/amd64/libc-dev-bin/2.11.1-0ubuntu7.2](https://launchpad.net/ubuntu/lucid/amd64/libc-dev-bin/2.11.1-0ubuntu7.2)

And now I feel like a noob... but we all make mistakes! :D

Now, after installing that, it has not mentioned anything of fglrx. I'm assuming that the "Hardware Drivers" application was searching for more than one file?

EDIT: Another edit, yes... It seems I've solved this by myself. O_O!!

Lol... That hasn't happened for a while.... Solving a problem after asking for help, without the help. I guess it's one of those things where you have to type it out or say it to figure out what to do...

ANYWAYS! Lol. If anyone else has this problem (btw, I'm on Linux Mint 9 KDE Edition, AMD 64 bit), try installing from the second link ([https://launchpad.net/ubuntu/lucid/amd64/libc-dev-bin/2.11.1-0ubuntu7.2](https://launchpad.net/ubuntu/lucid/amd64/libc-dev-bin/2.11.1-0ubuntu7.2)) And then go into "Hardware Drivers" and then install the FGLRX Driver.

-Don

---

### Post by mastablasta on 2011-02-15
Good morning then... :-) 
what is that and what does it have to do with driver problem? did you install the driver? What are you trying to do?

---

### Post by Donzieja on 2011-02-15
I am first trying to locate it, or a substitute. Then, I wish to install the drivers.

EDIT: It seems that I have found it here:

[http://buaya.klas.or.id/blankon/pool/main/e/eglibc/](http://buaya.klas.or.id/blankon/pool/main/e/eglibc/)

However, upon opening the .deb, the dependency: libc-dev-bin (= 2.11. 1-0ubuntu7.2) 

is not satisfiable.

I am terrible at resolving these types of issues, so any help would be appreciated.

Thanks,

-Don

---

### Post by mastablasta on 2011-02-15
why? are you trying to install proprietary drivers? if so then they are under System-Administration-hardware drivers.
 
if they are not there it means your card is not supported by the manufacturer or better yet the kernel, xserver,x is not supported by them. which means you use opensource drivers. which mean you should NOT install porprietary drivers as it can mess up your computers.
 
also if you need some libraries you can install it through synaptic. if it's not there then i am not sure you should be messing with it. :-O
if you want latest version of opensource drivers there is a PPA for that.

---

### Post by QIII on 2011-02-16
One of my machines has an HD 3200 series integrated GPU and the driver in the repo works just fine on that machine.

---

