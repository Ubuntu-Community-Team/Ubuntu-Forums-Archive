---
title: "wireless : broadcom 54g"
date: 2004-10-15
forum: Hardware &amp; Laptops
---

### Post by nilsmagnus on 2004-10-15
Hi,
I know that there is little support for broadcom 54g in linux, but is there anyone who has configured this wireless card successfully in ubuntu? Is there an easy way without recompiling ther kernel etc.?

My laptop(compaq 2108US) is working fine with ubuntu by the way. Just need wireless and a better solution for my radeon 320m igp

---

### Post by HungSquirrel on 2004-10-15
I *think* this guy is talking about your card.  I don't know how to implement the solution in Ubuntu, but here is **a** solution if not **the** solution.

[http://lineman.net/node/view/362](http://lineman.net/node/view/362)

---

### Post by ubuntu-geek on 2004-10-15
[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363)

Maybe check out that link..

---

### Post by nilsmagnus on 2004-10-15
Thank you both for quick replies.

Will spend the evening/night to set things up and test, and tell you how it went :)

---

### Post by daniels on 2004-10-16
ndiswrapper with the driver from the CD worked just fine for me with a Belkin-brand Broadcom PCMCIA card.  The only caveat was that I explicitly had to specify 'key off' every time, but this can be fixed by adding 'wireless_key off' to the wlan0 (or was it wifi0?) section in /etc/network/interfaces.

---

### Post by nilsmagnus on 2004-10-18
Nice. Just followed the ubuntu howto with a new kernel, edited /etc/modules to include ndiswrapper, and everything works smoothly.

Thanks for the help!

---

### Post by n00bie on 2004-10-21
Okay i need to know how to do the  same but i'm a complete linux n00b.

I know this is a pain but i need someone to post a step by step guide to getting this to work, this is only thing i need to get working and then i'll be rid of windows and i can start my linux adventure!!!!

What i think i should do (ignore completly to avoid getting angry! )
============================================
ndiswrapper emulates / wraps a windows driver, therefore if i get the xp driver and run ndiswrapper then my card should work.
First off how do you install Ndiswrapper all i can find is in root 
access NDISWrapper, run “make”
Well i've tried this but the ndiswrapper folder doesn't seem to want to play ball.
Coming from a completly windows background i assume that what we are trying to do is essetially run an exe file from dos, so we call up the commandline and type in the location of the file, this installs the program and then we can use it.
Therefore shouldn't there be a file called MAKE in the ndiswrapper folder?

==============================================

Any help would be very much appreciated as i love the look of Ubuntu but i cant properly begin to use it and therefore run into problems to overcome and learn linux unless i can get my card working, ultimatly no card no linux  :( 

Thanks 

Mark

---

### Post by nilsmagnus on 2004-10-21
hello n00ie:)

Everyone has been newbie once, and i am still one of them. 


First of all: have you installed ndiswrapper properly? Do youhave access to a lan/dsl connection with your linux? If so:

#sudo apt-get update
#sudo apt-get install ndiswrapper
#sudo ndiswrapper -i [yourwindowsdriverhere].inf
#sudo nano /etc/modules 
in this file you simply add the a line with "ndiswrapper"
edit your /etc/network/interfaces file as in the ubuntu tutorial, or as you like it
#sudo modprobe ndiswrapper
#sudo ifconfig wlan0 up

Hope you get it to work!

---

### Post by n00bie on 2004-10-21
thanks for the quick response, found out you have to type cd before accessing the directory LOL!

However no i get an error relating to the kernal i think, the text is:
===========================================
root@ubuntu:/home/mark # cd ndiswrapper root@ubuntu:/home/mark/ndiswrapper # make
make -C driver
make[1]: Entering directory `/home/mark/ndiswrapper/driver'
Can't find kernel sources in /lib/modules/2.6.8.1-3-386/build;
  give the path to kernel sources with KSRC=&lt;path&gt; argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/mark/ndiswrapper/driver'
make: *** [all] Error 2
root@ubuntu:/home/mark/ndiswrapper #
==========================================

also i'm not on a network as this wifi card connects to my network and the internet....

I therefore cant install over a network, how do i check if i've installed ndiswrapper correctly?

Any ideas?

---

### Post by n00bie on 2004-10-21
"Just followed the ubuntu howto with a new kernel, edited /etc/modules to include ndiswrapper, and everything works smoothly."

if someone can talk me through this i'd be forever greatful as it would allow me to stick with linux and not have to go back to windows.

---

### Post by FLeiXiuS on 2004-10-21
n00bie, 

You will need the kernel-2.6.8.1-3-386 source.  If you happen to know what source is great, if not.  Its the un-compiled code of a program, in this situation, the kernel 2.6.8-3-386.

To download the kernel source you can either check it out on [http://kernel.org](http://kernel.org) or the much easier way.

Open up a terminal and type:

```
sudo apt-get install kernel-source-2.6.8.1-3-386
```

I would rather have you update ubuntu to the latest kernel.  Kernel 2.6.9 was just released a few days ago.  Update your ubuntu by following these instructions...

[http://wiki.ubuntulinux.org/WartyWarthog/UpgradeNotes](http://wiki.ubuntulinux.org/WartyWarthog/UpgradeNotes)[/code]

---

### Post by n00bie on 2004-10-22
:oops:  i'm still completly stuck, frnakly i don't seem to have a clue with what i'm doing.

I've downloaded the new source (2.69) but can't install it over the old one, i can't seem to Configuring the kernel as 
========================================
There are several ways to configure the kernel. You will probably use "xconfig". Once you've changed to the /usr/src/linux directory, start it like this:

bash:/usr/src$ make xconfig
========================================
```

you have not yet configured your kernel!
please run some configurator.

```

frankly im in a mess and need Help!

So i type in make xconfig and get the error:
```

unable to find the QT installation

``` :oops:  :? 

i have the 2.69 source i just want to know how to install it, all the help sites that i've been on namely:[http://wiki.ubuntulinux.org/KernelHowto](http://wiki.ubuntulinux.org/KernelHowto)
say to use x config but the computer says i dont have it.

when i run make menu config i get the error
&gt;&gt; unable to find Ncurses Libraries

any help would be very appreciated.

THANK YOU everyone that's helped so far as i'm acting like a complete n00b I know but i just don't know what i'm doing, but i'm desperate for a linux laptop!

---

### Post by smalltowndoc on 2008-05-10
n00bie, i am as new to Ubuntu as you are. I have been trying to fix the broadcom bug also. As you rightly guessed, ndiswrapper is a small prog that emulates the windows drivers to work in linux. So the advantage is, if you have a driver problem, this prog can be of help. How to install ndiswrapper? I use Kubuntu, but the principle should be the same in Gubuntu also. I will tell you the easier way which is without using the terminal window, which though cool is better left to the experts. You open Apllication-system-adept installer (I think it can also be called synaptic manager). Here you will be asked for the password that you enetered when you installed the OS. Once you enter it, in the search box, type ndiswrapper. In the list below, you will get ndiswrapper and ndisutil (The utility files for ndiswrapper) and ndisgtk (The graphical user interface of ndiswrapper). Right click on those and click install. Then at the top, there is a button called apply changes. Click that. Swish, all the applications you requested for installation would have been installed. 
Close the adept/synaptic window. Press the application button-internet and you will see a new, wireless hardware option (This is actually the graphical interface, ndisgtk). Click that and it will ask, which file needs to be installed. You have to show the place where (either desktop or home) where your windows drivers are there. But you just need the .sys & .ini files to be shown to this prog . It will install it. If everything goes right, your card should connect.
PS. i am not an expert. So if anybody finds any fault, kindly correct it, so that others would be benefitted.

---

