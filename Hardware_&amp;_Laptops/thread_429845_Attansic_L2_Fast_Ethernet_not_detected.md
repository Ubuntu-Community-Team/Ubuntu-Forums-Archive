---
title: "Attansic L2 Fast Ethernet not detected"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by harvey28 on 2007-05-01
Hi everybodey, I have Laptop asus F5R and network adapter Attansic L2 Fast Ethernet. I have installed Fiesty Fawn and it didn't recognized it. I was looking for some drivers on web, but unsucessfully. Please help!
Thanks a lot.

---

### Post by barret_1986 on 2007-05-21
Hi :D 
I don't speak very well in english so i try to write without to many errors.

I have that notebook too, and i find drivers to Attansic L2 but i can't compile them, because i don't have other computer with linux :/ And i don't know anybody who has linux on his computer. I attached this file maybe someone compile it. :D

Did Faisty detect wifi card without problem or you made FF to detect that card??

---

### Post by rabossa on 2007-05-23
Em sembla a mi que en ixe nick vas a ser català, xD.

I recently bought a ASUS P5GC-MX MainBoard, and it has an Attansic L2 Fast Ethernet on it.
I compiled the module for make net working, and it just worked.

I attach the compiled module: 
[ATTACH]33221[/ATTACH]

You had to move it to /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko  (I suppose that this is for convention), and then ```
 insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko 
```

Then, your interface ethX, will appear on the NetworkManager.

Salutacions.

---

### Post by Afcs46 on 2007-05-26
> **rabossa said:**
> Em sembla a mi que en ixe nick vas a ser català, xD.

I recently bought a ASUS P5GC-MX MainBoard, and it has an Attansic L2 Fast Ethernet on it.
I compiled the module for make net working, and it just worked.

I attach the compiled module: 
[ATTACH]33221[/ATTACH]

You had to move it to /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko  (I suppose that this is for convention), and then ```
 insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko 
```

Then, your interface ethX, will appear on the NetworkManager.

Salutacions.



You`re the man!!! It works! Thanks a lot!
After months looking for a solution you are the precious help :D

Best Regards!

---

### Post by rabossa on 2007-05-29
Glad i could help. ;) :popcorn:

---

### Post by harvey28 on 2007-06-04
Hi everybodey, I found some drivers and it works! :D:D:D:D [http://launchpadlibrarian.net/7382416/L2-linux-driver_new.rar](http://launchpadlibrarian.net/7382416/L2-linux-driver_new.rar)

---

### Post by mfouad on 2007-06-06
Hi all ,

 i am thinking of buying asus f5r laptop , and saw some issues about its compatability with linux ,   did it completely work fine after the driver posted here ? i mean the WIFI , and ethernet and sound .


Thank you

---

### Post by tienhm on 2007-07-23
Hi all,
I have the same problem, but how can I install ubuntu with this type of network adapter without purchasing another one :confused:. Thanks a lot.

---

### Post by jdelcom on 2007-07-30
Hello. I have the same problem. I have a new desktop with Asus P5GC MX.
I tried with this driver and another given in other thread, and with both I get this reply:

insmod: error inserting 'lib..../atl2.ko': -1 Invalid module format

when I try with the src given by the mother drivers CD I get

Makefile 101: ***Linux kernel source not configured - missing config.h. Alto.

What else can I try? Without lan and internet, my desktop is worthless :(

Thanks for any help you can give me.

More detalis: Intel E2160, mobo mentioned, Ubuntu Desktop 64, kernel 2.6.20-15-generic.

---

### Post by ks_work on 2007-08-07
There is a newer version of the driver, that has a fix for later kernels.
I've had same problem with installing Attansic L2 network card driver on 2.6.21-31 kernel. Finally got it working after some fiddling with driver code.
More details here: [http://ihatecubicle.blogspot.com/2007/08/how-to-install-attansic-l2-network.html](http://ihatecubicle.blogspot.com/2007/08/how-to-install-attansic-l2-network.html)

good luck,
ks

---

### Post by iena on 2007-08-08
> **rabossa said:**
> Em sembla a mi que en ixe nick vas a ser català, xD.

I recently bought a ASUS P5GC-MX MainBoard, and it has an Attansic L2 Fast Ethernet on it.
I compiled the module for make net working, and it just worked.

I attach the compiled module: 
[ATTACH]33221[/ATTACH]

You had to move it to /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko  (I suppose that this is for convention), and then ```
 insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko 
```

Then, your interface ethX, will appear on the NetworkManager.

Salutacions.

Hi

I just tried this suggest and it works! Cool!

I applied it on Ubuntu installed in a Desktop PC with Asus P5LD2-X mobo

Thank you very much.

---

### Post by Blindraven on 2007-08-08
Attansic drivers only just got shipped with Fiesty (I have one in my M2V), don't tell me stupid Asus have made another nic undetected by anything.

---

### Post by iena on 2007-08-08
> **iena said:**
> Hi

I just tried this suggest and it works! Cool!

I applied it on Ubuntu installed in a Desktop PC with Asus P5LD2-X mobo

Thank you very much.

Only another question: every time I reboot my PC I need to retype the command
```
 sudo insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko 
```
why?

---

### Post by jspangler on 2007-08-09
> **jdelcom said:**
> 
insmod: error inserting 'lib..../atl2.ko': -1 Invalid module format



Try starting the command with sudo

---

### Post by jspangler on 2007-08-09
By the way, I Just did this on my girlfriends computer and it works great!

---

### Post by gizman on 2007-08-11
> **jspangler said:**
> Try starting the command with sudo
I have try it but it 's not work. I use mainboard P5GC-MX, E2160, and kernel 2.6.15-26-server

---

### Post by jspangler on 2007-08-11
What command are you using?

---

### Post by jspangler on 2007-08-11
> **iena said:**
> Only another question: every time I reboot my PC I need to retype the command
```
 sudo insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko 
```
why?

You have to tell this to start every time. 

To do this we change the file /etc/rc.local.

First back it up:

```
sudo cp /etc/rc.local /etc/rc.local.bak
```

Then:

```
gksudo gedit /etc/rc.local
```

Then insert the following above the last line (which says exit 0):

```
insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko
```

Make sure you put in your kernel version. Let me know if it works!

---

### Post by gizman on 2007-08-12
> **rabossa said:**
> Em sembla a mi que en ixe nick vas a ser català, xD.

I recently bought a ASUS P5GC-MX MainBoard, and it has an Attansic L2 Fast Ethernet on it.
I compiled the module for make net working, and it just worked.

I attach the compiled module: 
[ATTACH]33221[/ATTACH]

You had to move it to /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko  (I suppose that this is for convention), and then ```
 insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko 
```

Then, your interface ethX, will appear on the NetworkManager.

Salutacions.
  In Ubuntu 7.04 Desktop, it works properly, but in Ubuntu 7.04 server, when I use command "sudo insmod ...../atl2.ko" it fail and report "insmod ...... invalid module format".
Please help me!!!!!!! Thanks 
Sorry for my bad english

---

### Post by shekhark on 2007-08-22
Just wanted to record my sincere thanks to the folks in this thread for posting the attached file. It worked a charm after six hours of attempting to compile and install different drivers, which turned out to be completely unnecessary! Someone needs to tell the folks at Asus that the Linux drivers distributed on the CD that comes with the P5GC-MX are for the Attansic 1 and not the Attansic 2.

---

### Post by Nem Chua on 2007-08-23
> **jspangler said:**
> You have to tell this to start every time. 

To do this we change the file /etc/rc.local.

The file I found works for me is /etc/init.d/rc.local, which is called by /etc/rc2.d/S99rc.local when booting runlevel 2.

I don't know why there should be such a file as /etc/rc.local when the documentation says all init scripts should be in /etc/init.d

NC

---

### Post by jspangler on 2007-08-23
Cool, if that works for you then great. /etc/rc.local works well for me. I learned about it in this post: [http://ubuntuforums.org/showthread.php?t=504791&highlight=run+startup+as+root](http://ubuntuforums.org/showthread.php?t=504791&highlight=run+startup+as+root)

---

### Post by protenniser on 2007-09-11
Hi,
Praises to the one who rescued us from having the baddest nightmare in a linux world, can't use the internet. Hail in front of the one who gives us the compiler driver version and makes us happier, thank you very much, after having spent at least 4-5 hours of work on meaningless compilations and time in different forums, at the moment I was giving up saw your post, and it is like magic! :lolflag:

---

### Post by sou.1234321 on 2007-09-26
Dear Friends,

Please note that as per your advice I downloaded the attached atl2.ko file but was unable to move it to the folder you specified, i.e.
/lib/modules/<kernel version>/kernel/drivers/net/

because, everytime I am doing it, a warning box comes up and says that I don't have enough permission to write to that folder...!

Can somebody help me? I am using UBUNTU OS my motherboard is ASUS P5GC-MX

Please help...:confused:

---

### Post by IndyGunFreak on 2007-09-26
Did you put in your kernel version, or just type kernel version?  Also, the error seems to indicate you're not using sudo.

---

### Post by Nem Chua on 2007-09-26
If you are warned about not having enough permission, maybe you should try "sudo cp .." instead of "cp ..."

And to make it right without having to dig your kernel version, you might want to make it:

```

sudo cp atl2.ko /lib/modules/`uname -r`/kernel/drivers/net/

```

That should put it at the right place for the kernel under which you are currently running.

NC

---

### Post by sou.1234321 on 2007-09-26
Dear All,

Let me tell you that I am as idiot as a donkey in the LINUX world.

So kindly clear my doubts:

1. Firstly how to move a file in UBUNTU?
From XP, I can see that "atl2.ko" file is in D: drive.
My user name in UBUNTU is sou1234321.
Practically, I have always used cut & paste formula in Windows to move a file!!!
So, can someone be helpful enough to guide me in a step-by-step fashion?

---

### Post by venkat555 on 2007-09-27
can i nstall the same driver in linux driver for linux version 5 on asus motherboard , as the same is not detected in linux and the same is detected in XP.

---

### Post by IndyGunFreak on 2007-09-27
> **sou.1234321 said:**
> Dear All,

Let me tell you that I am as idiot as a donkey in the LINUX world.

So kindly clear my doubts:

1. Firstly how to move a file in UBUNTU?
From XP, I can see that "atl2.ko" file is in D: drive.
My user name in UBUNTU is sou1234321.
Practically, I have always used cut & paste formula in Windows to move a file!!!
So, can someone be helpful enough to guide me in a step-by-step fashion?

If you follow the instructions, then its been moved.  The instructions written by several users here are quite clear and about as simple as they can be.  Did you run the sudo command that NemChua mentioned?  If so, then the file was likely copied to the appropriate drive, and you just don't realize it.

Cutting and pasting as root, you can do it, but its not necessary in this case.

What exactly do you not understand?

IGF

---

### Post by sou.1234321 on 2007-09-27
Dear Friends,

At last I have succeded in establishing internet connection in UBUNTU.

Thanks a lot....

But I have few doubts...

Dear Friends, my internet connection is not at all consistent! It's working for 3/4 minutes then again no connection then again staying for 3/4 minutes then again going away...!

Is there any tuning, that I can do?

All the updates I am trying to do is showing failure due to inconsistent network!!!

I am sure that there is no problem with the provider/modem.

Please help...

---

### Post by venkat555 on 2007-09-27
My issue is ethernet card is not getting detected at all in linux 2.6:18-8.el5 enterprise version.  could any body throw some light on to get the ethernet card recognised in linux enterprise version 5.. i have tried all the methods, but the device is not getting recognised...

---

### Post by jspangler on 2007-09-28
I would check the ethernet cable you are using. Perhaps try hooking it to another computer, and see if you get stable service with that cable.

---

### Post by sou.1234321 on 2007-09-28
> **sou.1234321 said:**
> Dear Friends,

At last I have succeded in establishing internet connection in UBUNTU.

Thanks a lot....

But I have few doubts...

Dear Friends, my internet connection is not at all consistent! It's working for 3/4 minutes then again no connection then again staying for 3/4 minutes then again going away...!

Is there any tuning, that I can do?

All the updates I am trying to do is showing failure due to inconsistent network!!!

I am sure that there is no problem with the provider/modem.

Please help...

There is neither any problem with the ethernet wire. Because, in XP I am facing no such problems. Please help...:confused:

One thing worthy to mention is that:
Every time I boot into UBUNTU, for getting the net connection I have to type at terminal:

sudo insmod /lib/modules/2.6.20-15-generic/kernel/drivers/net/atl2.ko

Why is it so? Is there any other way out???

---

### Post by jspangler on 2007-09-28
> **sou.1234321 said:**
> There is neither any problem with the ethernet wire. Because, in XP I am facing no such problems. Please help...:confused:

One thing worthy to mention is that:
Every time I boot into UBUNTU, for getting the net connection I have to type at terminal:

sudo insmod /lib/modules/2.6.20-15-generic/kernel/drivers/net/atl2.ko

Why is it so? Is there any other way out???


There is a way to make it load automatically when it boots. To do this we change the file /etc/rc.local.

First back the file up through the terminal:

```
sudo cp /etc/rc.local /etc/rc.local.bak
```

Then:

```
gksudo gedit /etc/rc.local
```

Then insert the following above the last line (which says exit 0):

```
insmod /lib/modules/2.6.20-15-generic/kernel/drivers/net/atl2.ko
```

Hope that helps.

---

### Post by sou.1234321 on 2007-09-28
Dear jspangler,

Thanks a lot for the prompt help...

As I have said, my [COLOR="Red"]**[SIZE="4"]Internet connection is not remaining stable/consistent[/SIZE]**[/COLOR].

It's coming -> then going away -> then again coming. It's behaving on its own!!!:confused:

Everytime I am trying to update the UBUNTU, it's failing due to the unstable connection.

I am getting fed up everytime. Again starting the update, but again with same fate.... :(

PLEASE HELP me out.....

---

### Post by jspangler on 2007-09-28
I don't have any ideas about that. Maybe you should start a new post in the forums so that other people see your problem and can help.

---

### Post by ks_work on 2007-10-04
> **sou.1234321 said:**
> Dear jspangler,

Thanks a lot for the prompt help...

As I have said, my [COLOR="Red"]**[SIZE="4"]Internet connection is not remaining stable/consistent[/SIZE]**[/COLOR].

It's coming -> then going away -> then again coming. It's behaving on its own!!!:confused:

Everytime I am trying to update the UBUNTU, it's failing due to the unstable connection.

I am getting fed up everytime. Again starting the update, but again with same fate.... :(

PLEASE HELP me out.....

I assume this is due to diffferent version of kernel, can you provide contents of your /boot directory ?
Also keep track of [this thread]("http://ihatecubicle.blogspot.com/2007/08/how-to-install-attansic-l2-network.html"), for updates on Attansic L2 driver

cheers,
ks_work

---

### Post by jaderubini on 2007-10-13
Thank you for the help!!!

---

### Post by arupdg on 2007-10-13
Hi,

I posted the following in the linuxquestions forum and was directed to this thread:

Hi,

I have just bought a new PC with this config:
P4 3.2GHz(HT) (64bit)
ASUS P5GC-MX motherboard
1GB RAM
160GB SATA HDD (Linux partition about 50GB)
I loaded ubuntu 6.06 LTS from a CD
It does not recognise the Realtek sound card or the Attansic L2 ethernet card both of which are built on to the mother board. I also have a Pinnacle Studio VCD card on a PCI bus which is not recognised either, but that can wait. At the moment the ethernet card is proving to be a big issue.

I tried to install the driver from the vendor disc but was flummoxed as the readme instructions referred to a non-existent tar file. I then went to the ASUS web site (using Windows) and downloaded what I thought was the latest drivers (nearly 30MB!). Unfortunately it is the same guff. So I am back to square 1.

I have been following some threads on this topic but I am none the wiser and it seems the solutions are only partial.

I had run Kanotix on my old PC which had a vanilla ethernet card and it was recognised and accessed without a hitch.

I thought ubuntu on a new PC would be a breeze. I wonder if Linux is all that it is made out to be?


As you can see I have a similar problem. I tried the solutions I got from this thread but I am still stuck
because  that atl2.ko did not work and gave a wrong version error. May be because I am using 6.06 with kernel version 2.6.15.

I tried to follow the vendor supplied CD instructions by issuing the command 'make install' in the src directory. The bash returned an error that 'make' was not understood. Also there is a Makefile in the src directory. My very limited knowledge of Linux does not allow me to go any further. Any suggestions?

BTW I could install the sound drivers successfully from the CD by going to the appropriate directory and clicking on the file named install.

Also I find from the system manager that my PCI video capture card has been recognised!

Wonders will never cease!

---

### Post by jspangler on 2007-10-13
arupdg,

First off, you need to install the component called build-essential, which you should be able to install by placing the ubuntu cd into the drive and adding it to the repositories when it asks. That should allow you to do the make command.

Second, what command did you type in that gave you the wrong version error?

Keep us informed.

---

### Post by arupdg on 2007-10-14
Hi All,

SUCCESS! I am emailing you from my Ubuntu Firefox browser. What did I do?

I had to first put back the Ubuntu CD and load all those packages NOT
loaded in initial install. This included the 'make'. Then I followed
the instructions which came with the downloaded Linux Driver package
from Attansic. Always I have to use the 'sudo' prefix to get superuser
privileges. I had to manually move the compiled atl2.ko driver to the
designated directory. And I was online.

Truly, the forums were a big help and if my little experience is of any use to others I will be happy.:guitar:

I think Atheros needs to get its act together as its readme was very confusing. It starts by talking of RPM. I came to know this is specific to RedHat. Then it talked of ungzipping a file which was not there anywhere.But I did see a src directory with lots of .c and .h files and a Makefile. I am literate enough to understand these were source codes. So I ran the make install and got a raspberry:confused: Back to Ubuntu basics and a book on linux before I cottoned on to the :idea: missing developers modules. Back to the Ubuntu CD and then ... SUCCESS. I am chuffed:biggrin:

---

### Post by jspangler on 2007-10-14
You're learning fast! Next time you want to install something it will be a piece of cake.

---

### Post by arupdg on 2007-10-14
Naah, Now I am stuck trying to load a Shockwave plug-in for Firefox. Another problem is that any upgrade to the kernel and I have to go through the whole thing again. I hit this when I upgraded Ubuntu. But tell me can this happen if I add Java Runtime?
Also Synaptic loader upgrades my Firefox to 1.5. something but Firefox itself says the latest is 2.0.something. I downloaded the gz file but Synaptic refuses to acknowledge its existence!

I still have a lot to learn#-o

---

### Post by jspangler on 2007-10-14
This is really another topic. You should put future questions in a new thread so more people will see it :-)

That being said, go to your terminal. You can get this by going to Applications > Accessories > Terminal.

Type in:

```
sudo apt-get update
```

Then:

```
sudo apt-get upgrade
```

And see if that updates your firefox. To install flash, download it from the internet (the linux version, shouldn't be too hard to find). If they have a file for Debian, just download and double-click that. If not, follow the install directions (It might be a bin file that you just need to double click).

---

### Post by arupdg on 2007-10-14
As I said I have a lot to learn:(

New thread started

---

### Post by arupdg on 2007-10-15
I didn't start a new thread because I found this:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
Cheers

---

### Post by prudvimts on 2007-10-18
Invalid module format


i get this error again and again

---

### Post by amar123 on 2007-11-11
I have read all posts on this topic with interest but haven't found a solution yet. My problem is the same as arupdg except that I am using openSUSE 10.3, not ubuntu. Do I need to visit a different forum?

If not, here are my details:

P4 1.6 GHz
ASUS P5GC-MX motherboard
1GB RAM
160GB SATA HDD (Linux partition 30 GB)

I tried rabossa's solution and it works with Linux Mint. Unfortunately, it doesn't work with openSUSE 10.3.

ks_work's solution of "fiddling with the driver code" ([http://ihatecubicle.blogspot.com/2007/08/how-to-install-attansic-l2-network.html](http://ihatecubicle.blogspot.com/2007/08/how-to-install-attansic-l2-network.html)) is not a newbie's cup of tea. So I have given it up :-(

Is there a simpler way of making it work on openSUSE 10.3? Or should I switch back to Mint?

---

### Post by amar123 on 2007-11-11
I could not solve the network problem in openSUSE using Attansic L2 Fast Ethernet adapter. So, I decided to install ubuntu instead. However, getting the Internet to work in ubuntu was not a piece of cake as I had expected it to be. It took me several hours to fix the problem, but I finally tasted success. 

I thought of sharing my experience with others (read newbies like me) who are facing similar problems with Attansic L2 Fast Ethernet card. Please note that I am a complete newbie and I have simply compiled this information from various forums. In addition, these may not be the best practices to follow, so if you are unsure please consult an expert before following these steps. 

1. Go to System -> Administration -> Users and Groups.

2. Select "root" and then click on Properties.

3. Change root's password to any password of your choice. Confirm the new password.

4. Click on "Generate random password" and change the random password to the new password in step 3.

(4a. Under "User Privileges," I had checked all the boxes. Do it if you want to.)

5. Click OK.

6. Go to System -> Administration -> Login Window.

7. Under Security, check "Local system administrator login."

8. Restart or log off your sytem. This time you should be able to log in as "root".

9. I copied the "atl2.ko" file that rabossa posted (see page 1 of this thread) to the following directory: lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl2.ko (You need to replace <KERNEL VERSION> with your ubuntu version number -- mine is "2.6.20-15-generic")

10. Open Terminal Server and type the following code: insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl2.ko

11. Then type the following code: cp /etc/rc.local /etc/rc.local.bak

12. Then type this code: gedit /etc/rc.local

13. A new file will open. Insert the following code above the last line (which says exit 0): insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl2.ko

14. Save the file.

Your internet should be up and running by now.

For security reasons, remember to login as a normal user and uncheck "Local system administrator login" in Step 7.

Please let me know if it works. If it doesn't, unfortunately I can't help.

My thanks to all those whose posts enabled me to connect to the Internet using Attansic L2 Fast Ethernet adapter, especially rabossa and arnieboy.

I would appreciate it if someone can help me in installing the Attansic L2 Fast Ethernet driver in openSUSE 10.3.

---

### Post by Stompen on 2007-12-01
Oh yes. The ubuntu forums rule. I search for "f5r" because my laptop cant use it's wireless network. This thread comes up, and VOILA! 

:D Thanks guys

---

### Post by matinj on 2008-01-21
Hi all,
I have a P5GC-MX with Attansiv L2, and linux Suse10.1, kernel 2.6.16
I did your comments (copy the atl2.ko to the mentioned path)and run
insmod /lib/..../net/atl2.ko, sudo insmod /lib/.../net/atl2.ko,  
insmod /lib/.../net/atl.ko (I renamed atl2.ko  to  atl.ko!!) but all of them were not successful and i received "Invalid module".
Any Idea????????????? This is Urgent!
Thanks

---

### Post by signo82 on 2008-02-05
> **venkat555 said:**
> My issue is ethernet card is not getting detected at all in linux 2.6:18-8.el5 enterprise version.  could any body throw some light on to get the ethernet card recognised in linux enterprise version 5.. i have tried all the methods, but the device is not getting recognised...

I have the same problem...
How can we solve?

---

### Post by Vnepomuceno on 2008-03-04
Hi all!
I have an Asus F5R laptop with a Attansic L2 Fast Ethernet and using the driver that rabossa attached, but as I'm using Ubuntu 7.10, it returned me this error message:

```
insmod: error inserting 'lib..../atl2.ko': -1 Invalid module format
```

I've read all the thread but I didn't find any solution to this problem... Can anyone help me? Is that this is urgente because I have a C project for university, and I have to use Ubuntu... and laptop without Internet, for developing projects, just don't work :)

Thanks in advice

---

### Post by Vnepomuceno on 2008-03-05
Ouhh, I forget to tell you, I'm a portuguese student, so, if there are any errors in my replies, please don't be scared :)

---

### Post by jspangler on 2008-03-07
OK, I think everybody here needs to make the module from the source code.

Here's how. First download the file to your home directory. Open a terminal.

Do the following:

```
tar zxf L2-linux-driver.tar.gz
```

```
cd L2-linux-driver/src/
```

```
sudo make install
```

```
insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
```

This is from memory, because I installed this on my girlfriend's computer. Let me know if it doesn't work.

---

### Post by jspangler on 2008-03-07
> **Vnepomuceno said:**
> Hi all!
I have an Asus F5R laptop with a Attansic L2 Fast Ethernet and using the driver that rabossa attached, but as I'm using Ubuntu 7.10, it returned me this error message:

```
insmod: error inserting 'lib..../atl2.ko': -1 Invalid module format
```

I've read all the thread but I didn't find any solution to this problem... Can anyone help me? Is that this is urgente because I have a C project for university, and I have to use Ubuntu... and laptop without Internet, for developing projects, just don't work :)

Thanks in advice

Hi,

I think this driver should be included in the Gutsy kernel. If it's not working for you, you might first try other problems. One thing is for sure, the driver attached at the beginning of this topic is kernel and distro specific. It will not work for Gutsy or Suse or any other distribution.

You might make sure your networking problem doesn't come from somewhere else. 

To get an idea, run in terminal:

ifconfig

and print the output here.

---

### Post by LinkyParky on 2008-04-22
> **jspangler said:**
> OK, I think everybody here needs to make the module from the source code.

Here's how. First download the file to your home directory. Open a terminal.

Do the following:

```
tar zxf L2-linux-driver.tar.gz
```

```
cd L2-linux-driver/src/
```

```
sudo make install
```

```
insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
```

This is from memory, because I installed this on my girlfriend's computer. Let me know if it doesn't work.

i get this when i try the same steps as u :


Makefile:114: *** Compiler not found.  Stop.

---

### Post by LinkyParky on 2008-04-22
> **jspangler said:**
> OK, I think everybody here needs to make the module from the source code.

Here's how. First download the file to your home directory. Open a terminal.

Do the following:

```
tar zxf L2-linux-driver.tar.gz
```

```
cd L2-linux-driver/src/
```

```
sudo make install
```

```
insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
```

This is from memory, because I installed this on my girlfriend's computer. Let me know if it doesn't work.

i get compiler not found when sudo make install

---

### Post by toster1984 on 2008-04-23
> **rabossa said:**
> Em sembla a mi que en ixe nick vas a ser català, xD.

I recently bought a ASUS P5GC-MX MainBoard, and it has an Attansic L2 Fast Ethernet on it.
I compiled the module for make net working, and it just worked.

I attach the compiled module: 
[ATTACH]33221[/ATTACH]

You had to move it to /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko  (I suppose that this is for convention), and then ```
 insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko 
```

Then, your interface ethX, will appear on the NetworkManager.

Salutacions.



Thank you! :guitar:

Gracias tio, me has servido de gran ayuda! ;)

---

### Post by LinkyParky on 2008-04-23
> **toster1984 said:**
> Thank you! :guitar:

Gracias tio, me has servido de gran ayuda! ;)



i got the same issue - invalid 
couldn't compiler..stop

---

### Post by LinkyParky on 2008-04-25
Makefile:65: *** Linux kernel source not found.  Stop.


any help

---

### Post by Cfr..sv on 2008-04-30
same problem here:
Makefile:101: *** Linux kernel source not configured - missing config.h.
heeelp!

---

### Post by ogre11 on 2008-04-30
> **LinkyParky said:**
> Makefile:65: *** Linux kernel source not found.  Stop.


any help

Same here.  When I use package manager to attempt to add "linux" or "linux-kernel-devel" I get an error because it cannot connect to the internet to download portions!

---

### Post by ogre11 on 2008-04-30
Another error down, another error appears.

To get past the "Makefile:65: *** Linux kernel source not found. Stop." error, I started the Package Manager (System->Administration -> Synaptic Package Manager); then went into the Development section and added the following:

linux-headers-2.6.15-26
linux-headers-2.6.15-26-386
linux-headers-386

Those all installed from the CD.

(Note: I'm pretty sure those who are getting "Compiler Not Found" need to do the same, but install build-essential from the development category).

Now when I get to the last line of instructions (the insmod), I get a new error:

insmod: error inserting '/lib/modules/.../atl2.ko': -l Invalid module format

Any ideas on what causes that one?

---

### Post by ogre11 on 2008-04-30
Finally, I got it!  The reason the module insmod was failing was because I had a different version.  I had forgotten to copy over the new file that I had just compiled.  Yay, stuff.  :)

---

### Post by iomicifikko on 2008-05-15
Hi guys, i just installed Ubuntu 8.04 on a machine with this P5GC-MX/1333 asus motherboard. Differently from what i read in the past posts, network card is detected (as eth0), driver is loaded and used (network applet->right-click->connection information-> "Driver: ATL2") but my connection simply doesn't work. 
I have tryed to change settings with "manual configuration" deselecting "roaming mode" in the card properties, and choosing DHCP but nothing is changed (also tryed static...). I just can't connect.

Any idea?

Ps:before installing Hardy i've tryed the last Fedora 9 live cd and everything had worked fine.


Thank u!

---

### Post by gustavo.kawamoto on 2008-05-25
> **iomicifikko said:**
> Hi guys, i just installed Ubuntu 8.04 on a machine with this P5GC-MX/1333 asus motherboard. Differently from what i read in the past posts, network card is detected (as eth0), driver is loaded and used (network applet->right-click->connection information-> "Driver: ATL2") but my connection simply doesn't work. 
I have tryed to change settings with "manual configuration" deselecting "roaming mode" in the card properties, and choosing DHCP but nothing is changed (also tryed static...). I just can't connect.

Any idea?

Ps:before installing Hardy i've tryed the last Fedora 9 live cd and everything had worked fine.


Thank u!

Same problem here!

---

### Post by almaalom on 2008-05-26
I have managed to use Attansic L2 on my P5klm-cm, the "magic" was not simple:

in usr/src/<your-kernel>/include/linux directory:
sudo ln -s autoconf.h config.h

ant then build it like this:
sudo make KBUILD_NOPEDANTIC=1 install

---

### Post by doublesunflower on 2008-06-13
Hi i am a newbee

i did try make install with different source and with the one from my cd it ask me config.h
and the one from the asus.com

the one from this forum give me this error
frank@frank-desktop:~/Desktop/l2-linux-v1.0.40.4/src$ sudo make install
make: Warning: File `Makefile' has modification time 5.5e+07 s in the future
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/frank/Desktop/l2/src                    modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/frank/Desktop/l2/src                   /Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/frank/Desktop/l2/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
frank@frank-desktop:~/Desktop/l2-linux-v1.0.40.4/src$



i did tried also the atl2.ko from that forum and it wasn t working
insmod: error inserting '/lib/modules/.../atl2.ko': -l Invalid module format

i did that with ubuntu 8.04 and kubuntu 8.04 both on 64 bit.
P5GC-MX and E2200

thank you very much

---

### Post by phockschann on 2008-06-20
Same here, it worked with 7.10 , but since i tried to install 8.04 and see network is down, although i came back to 7.10 the network failed to start, and when i tried to do what is said on this forum i have an error mesage for insmod command " invalide module format".
So...What the heck is going on here? the new 8.04 modified something on my motherboard that make any linux version to not be able to connect to the network ?! Shame on you, 8.04 ! if you did it and i am 95% sure that it is the new Ubuntu`s fault.

---

### Post by ssj4Gogeta on 2008-06-24
> **iomicifikko said:**
> Hi guys, i just installed Ubuntu 8.04 on a machine with this P5GC-MX/1333 asus motherboard. Differently from what i read in the past posts, network card is detected (as eth0), driver is loaded and used (network applet->right-click->connection information-> "Driver: ATL2") but my connection simply doesn't work. 
I have tryed to change settings with "manual configuration" deselecting "roaming mode" in the card properties, and choosing DHCP but nothing is changed (also tryed static...). I just can't connect.

Any idea?

Ps:before installing Hardy i've tryed the last Fedora 9 live cd and everything had worked fine.


Thank u!

Exactly the same problem.

I even installed the package:
[http://packages.ubuntu.com/hardy/atl2-source](http://packages.ubuntu.com/hardy/atl2-source)
including all the dependencies. I wonder if someone can help.

PS: I'm running kubuntu 8.04 along with Vista Ultimate and XP Pro (all 32 bit) and I don't know anything about Linux. I just installed it. So it'll be great if someone can provide me step by step instructions.

My ethernet card is Atheros L2 Fast Ethernet and mobo is Asus P5GC-MX/1333

---

### Post by satanas147 on 2008-06-24
> **doublesunflower said:**
> Hi i am a newbee

i did try make install with different source and with the one from my cd it ask me config.h
and the one from the asus.com

the one from this forum give me this error
frank@frank-desktop:~/Desktop/l2-linux-v1.0.40.4/src$ sudo make install
make: Warning: File `Makefile' has modification time 5.5e+07 s in the future
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/frank/Desktop/l2/src                    modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/frank/Desktop/l2/src                   /Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/frank/Desktop/l2/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
frank@frank-desktop:~/Desktop/l2-linux-v1.0.40.4/src$



i did tried also the atl2.ko from that forum and it wasn t working
insmod: error inserting '/lib/modules/.../atl2.ko': -l Invalid module format

i did that with ubuntu 8.04 and kubuntu 8.04 both on 64 bit.
P5GC-MX and E2200

thank you very much
I all, I have exactly the same problem and the same messages.
What can be done to fix the issue?
Thanks for your help & feedbacks

---

### Post by Master Chief on 2008-06-27
*make: Warning: File `Makefile' has modification time 5.5e+07 s in the future*

The cause of this error is a broken/illegal timestamp (future date) which if I'm correct was something like 2010.  A simple fix is to update (touch) the files with: 

**touch filename**

[I]scripts/Makefile.build:46: *** CFLAGS was changed in "/home/frank/Desktop/l2/src /Makefile". Fix it to use EXTRA_CFLAGS. Stop.
[/I]
Fix it by rename all occasions of **CFLAGS** to **EXTRA_CFLAGS**

Also comment the following line:

CFLAGS += $(CFLAGS_EXTRA)

out like this:

#CFLAGS += $(CFLAGS_EXTRA)

You should also get a few other errors; one about DBG not being defined (in at.h?) which you can solve by adding DBG as environment variable like this:

**export DBG=0**

and another one about **eth_copy_and_sum** being explicitly defined, but I forgot 
the other one (just comment the offending lines out with /*   */).

And finally, the following line in Makefile doesn't work either:
**man -c -P'cat > /dev/null' $(MANFILE:.$(MANSECTION)=) || true** 

You can either remove the line, or comment the line out by adding a **#** in front of it.

Don't panic when things don't work right away, you can always load the driver manually with:

sudo modprobe atl2

Or remove it with:

sudo modprobe -r atl2

**Note:** I use modprobe instead of insmod because the former is more advanced (cleverer).

How do I know if *atl2* is loaded?  Simple, use: **lsmod|grep atl2**
which shows something like:

Module                  Size  Used by
atl2                   63500  2

or you can type **dmesg | grep atl2** in a console which should dump some debug/log lines about the *Attansic* module/driver (giving you clues as to if the driver is successfully loaded or not).

TIPS:

You can restart your network with:

sudo /etc/init.d/networking restart

You can check if your network adapter is DISABLED with:

sudo lshw -C network

Do you see something like: *-network:0 UNCLAIMED

Use: sudo modprobe forced ethN (where N is either 0 or 1).

Make sure that your driver isn't blacklisted in:

/etc/modprobe.d/blacklist 

and that /etc/network/interfaces list:

auto ethN
iface ethN inet dhcp

when you use DHCP to get your ip# from.

ifconfig looks strange???:

ethN (IP v6)
ethN:avahi (IP v4)

You can also (but why would you?) disable IP v6 by commenting out a single line in aliases (see other forum postings) and fix your udev rules with /usr/lib/udev/fix-persistent-net.pl

And my final tip for today: try man ethtool ;)

[U]
ASUS P5GC-MX (1333) LAN port LED indications:[/U]

ACT/LINK LED (left/top)
============
OFF    (No Link)
OANGE  (10/100Mbps connection)
ORANGE (10/100Mbps connection)

Speed LED (right/top)
=========
OFF   (No Link)
OFF   (10Mbps connection)
GREEN (100Mbps connection)

Make sure you enabled the interface in the BIOS (press delete key at startup to enter setup) like this:

Onboard PCIEX 10/100MbLAN  [ENABLED]
LAN Option ROM             [DISABLED]

You can check the adapter in Windows (install driver first) if nothing goes, that should confirm the cable/connection being all OK.

---

### Post by mpascall on 2008-07-05
Hi Master Chief,

Thanks for your help.  Your suggestions have let me build my driver with no errors, but I'm still not getting it to see my router/dhcp server.

I have the exact same motherboard described above(asus p5gc-mx/1333) with same on board lan adapter.

After going through the steps you suggest, the lan LED's do not light up.  If I install XP and the driver on the CD they do light up, and it gets it config from my router/dhcp server (siemens speadstream 4100b ethernet adsl modem) and am actually using it right now to post this.

I'm using a fresh install of Ubuntu 8.04 64-bit, with no config changes except to make eth0 use DHCP, which I did using the Network config gui.

Here's an output of my latest attempt:

[COLOR=DimGray][SIZE=1]
marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ sudo make install
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/marcus/Desktop/l2-linux-v1.0.40.4/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
# remove all old versions of the driver
find /lib/modules/2.6.24-16-generic -name atl2.ko -exec rm -f {} \; || true
find /lib/modules/2.6.24-16-generic -name atl2.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl2.ko /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl2/atl2.ko
/sbin/depmod -a || true
install -D -m 644 atl2.7.gz /usr/share/man/man7/atl2.7.gz
# man -c -P'cat > /dev/null' atl2 || true

marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ lsmod|grep atl2
atl2                   37528  0 

marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5877
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1e:8c:9f:77:08
Sending on   LPF/eth0/00:1e:8c:9f:77:08
Sending on   Socket/fallback
grep: /etc/resolv.conf: No such file or directory
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1e:8c:9f:77:08
Sending on   LPF/eth0/00:1e:8c:9f:77:08
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
                                                                         [ OK ]

marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ dmesg | grep atl2

marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:9f:77:08
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=1.0.40.3 duplex=full firmware=L2 latency=0 link=yes module=atl2 multicast=yes port=twisted pair speed=100MB/s
marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ more /etc/network/interfaces
auto lo
iface lo inet loopback



iface eth0 inet dhcp

auto eth0

marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:9f:77:08  
          inet6 addr: fe80::21e:8cff:fe9f:7708/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:3498 (3.4 KB)  TX bytes:0 (0.0 B)
          Memory:dffc0000-e0000000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:8c:9f:77:08  
          inet addr:169.254.5.24  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:dffc0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79360 (77.5 KB)  TX bytes:79360 (77.5 KB)


marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ uname -r
2.6.24-16-generic

marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ [/SIZE][/COLOR]

Any ideas what I'm doing wrong?  This is my first time using Ubuntu.  I have some experience with HP-UX from many years ago, and have probably forgotten anything useful.  But I'm fairly bright and resourceful, so I'm not asking for step by step instructions.  I don't mind rooting around a bit, if you don't mind pointing me in some possible directions...  

Thanks!
-Marcus

edit: 

I grep'd my dmesg incorrectly above.  Here's what the output is:

[COLOR=DimGray][SIZE=1]marcus@marcus-ubuntu:/etc/modprobe.d$ dmesg | grep ATL2
[   32.278018] ATL2: eth0 NIC Link is Up<100 Mbps Full Duplex>[/COLOR] [/SIZE]

Also tried turning IPv6 off, and tried my old Linksys router.  Still no lights on the LAN adapter under Ubuntu.  Lights are on under XP.

Also tried using a fixed IP address and trying to ping my router.  No luck.

---

### Post by mpascall on 2008-07-05
One other thing that I forgot to mention:

After modifying, as you recommeneded, the Makefile and the .c file that were giving errors, I tried a make and this was my output:

[COLOR="DimGray"][SIZE="1"]
marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ make
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/marcus/Desktop/l2-linux-v1.0.40.4/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/marcus/Desktop/l2-linux-v1.0.40.4/src/at_main.o
  CC [M]  /home/marcus/Desktop/l2-linux-v1.0.40.4/src/at_hw.o
  CC [M]  /home/marcus/Desktop/l2-linux-v1.0.40.4/src/at_param.o
  CC [M]  /home/marcus/Desktop/l2-linux-v1.0.40.4/src/at_ethtool.o
/home/marcus/Desktop/l2-linux-v1.0.40.4/src/at_ethtool.c:426: error: unknown field &#8216;get_perm_addr&#8217; specified in initializer
/home/marcus/Desktop/l2-linux-v1.0.40.4/src/at_ethtool.c:426: error: &#8216;ethtool_op_get_perm_addr&#8217; undeclared here (not in a function)
make[2]: *** [/home/marcus/Desktop/l2-linux-v1.0.40.4/src/at_ethtool.o] Error 1
make[1]: *** [_module_/home/marcus/Desktop/l2-linux-v1.0.40.4/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
marcus@marcus-ubuntu:~/Desktop/l2-linux-v1.0.40.4/src$ [/SIZE][/COLOR]


So I commented out the offending line from at_ethtool.c.  Then it compiled without error.  Looking back, that is probably the cause of my issue.  Any ideas why I'd be getting this error when you didn't?

Thanks!
-M

---

### Post by Master Chief on 2008-07-06
"*error: unknown field &#8216;get_perm_addr&#8217; specified in initializer*" means that 'get_perm_addr' no longer exists.  The reason for this is that it has been removed from [COLOR="SeaGreen"]ethtool_ops[/COLOR] a number of kernel version back (it had only one caller).

Check out this file:
```
 
/usr/src/`uname -r`/include/linux/ethtool.h
```
In short; you must take it out ;)

---

### Post by ssj4Gogeta on 2008-07-07
Somebody please help me too. :(

Pls. see my post above. My adapter is detected, but even when I turn my modem on, it still stays at "disconnected". There is no problem with modem/wiring, cuz they work perfectly with windows. Once I booted into kubuntu and it magically started showing "connected" (and i didnt do anythign different that time). but i cudn't set up my PPPOE. then i rebooted, and it returned to its normal "disconnected".

Please give me detailed instructions cuz i dont know anything about Linux. Also, I'd be grateful if you can help me setup my PPPOE connection.

---

### Post by Master Chief on 2008-07-07
> Somebody please help me too. 

I do what I can, but I don't use this Asus P5GC-MX/1333 motherboard myself, but I compiled it for someone I know.

Also, there are now at least two different driver versions out in the wild, one from the official CD (the same as the website) and the other is the one from RedHat developer Chris Snook <csnook@redhat.com> 
Here's his webpage: [http://people.redhat.com/csnook/atl2/](http://people.redhat.com/csnook/atl2/)

Read the files, patch and compile it, but make sure to enter [COLOR="Red"]M[/COLOR] (short for module) when it generates the .config file for you!

---

### Post by mpascall on 2008-07-08
> **Master Chief said:**
> In short; you must take it out ;)

Ok, thanks.  That's what I did.  I wanted to be sure that was right.  

I'm going to try Chris Snook's driver, since it looks like I have the same problem as ssj4Gogeta.  I'll post my results.

Thanks!

---

### Post by ssj4Gogeta on 2008-07-08
> **Master Chief said:**
> I do what I can, but I don't use this Asus P5GC-MX/1333 motherboard myself, but I compiled it for someone I know.

Also, there are now at least two different driver versions out in the wild, one from the official CD (the same as the website) and the other is the one from RedHat developer Chris Snook <csnook@redhat.com> 
Here's his webpage: [http://people.redhat.com/csnook/atl2/](http://people.redhat.com/csnook/atl2/)

Read the files, patch and compile it, but make sure to enter [COLOR="Red"]M[/COLOR] (short for module) when it generates the .config file for you!


Thanks.:) but i don't know how to patch/compile. :( can you or mpascall guide me? i downloaded the 2.0.4 version patch and the tar. but now what do i do? please help.

---

### Post by Master Chief on 2008-07-08
But I do, so please keep an eye on: [http://ubuntuforums.org/showthread.php?p=5310139](http://ubuntuforums.org/showthread.php?p=5310139)

---

### Post by Master Chief on 2008-07-08
Done!  I attached both working copies for 32 and 64 bit Ubuntu editions!

---

