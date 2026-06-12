---
title: "My Canon Pixma iP1000 is working now! (with a third-party repository)"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by ReyPeste on 2007-01-10
I read a lot of How-tos and downloaded packages with dependency problems and the like, but then I tried this solution which was very straight forward and easy! I hope it helps.

This is how I got my **Pixma ip1000** to work on Kubuntu Edgy. 

I found this page with resources for a lot of Canon printers on linux:
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

**But to explain it briefly:**
1. I added the Ubuntu repository mentioned there to /etc/apt/sources.list:
> deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

2. I installed the following packages:
> sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj

3. Then I went to the Stystem Settings > Printers > Add
I chose the printer location and then it asked me for the manufacturer an model
The Pixma iP1000 **was not** in the list, so I chose **Other...**

4. I found the driver at /usr/share/ppd/pstocanonbj/
it was called *canonpixmaip1000.ppd*

And now I was ready to go! Test page printed without problems!
I hope this is info is helpful.

---

### Post by PurplePenguin on 2007-01-10
This is a great little howto that you've put together.  Canon printers are brutal to get going properly... I'm sure you'll help a ton of people with this!

One tiny problem, though, is that the link appears to be dead (for me, anyway).  hopefully it's either temporary or there's a mirror somewhere!

---

### Post by ReyPeste on 2007-01-10
Waaaah! You are right! I made a small typo! I will edit now! it should say tokyo-u instead of just tokyou.  There were packages for many other canon printers (pixus and pixma)! (Hey Takushi Miyoshi- thank you!). There! I've corrected it.

---

### Post by nrayever on 2007-01-28
hey man this works like a charm!!!, thanks a lot for the effort, you should make it a howto!! :KS :KS

thanks a lot

nrayever

---

### Post by lemmy999 on 2007-03-07
Ray

Great work dude!! Its only taken me about 18 months to get my printer working!!

Another reason to get rid of Window$!!

---

### Post by diskotek on 2007-04-02
> **ReyPeste said:**
> I found this page with resources for a lot of Canon printers on linux:
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

**But to explain it briefly:**
1. I added the Ubuntu repository mentioned there to /etc/apt/sources.list:


2. I installed the following packages:


3. Then I went to the Stystem Settings > Printers > Add
I chose the printer location and then it asked me for the manufacturer an model
The Pixma iP1000 **was not** in the list, so I chose **Other...**

4. I found the driver at /usr/share/ppd/pstocanonbj/
it was called *canonpixmaip1000.ppd*

And now I was ready to go! Test page printed without problems!
I hope this is info is helpful.

for newbies like me: i think after editing etc/apt/source.list, it needed to update it: (if you are editing update list via mousepad/gedit/kate)
> apt-get update

it worked for me like that... thanks to everyone who made this driver and who let us know :D
takushi you are hero :)
it works well with xubuntu 6.10

---

### Post by hamenarin on 2007-04-11
It works also on my Feisty Fawn Beta 3!
Thanks!

---

### Post by PaulRay on 2007-05-11
This worked like a charm. 
Just be sure that you double check that all the recommended files are installed for ubuntu and not debian (I missed that part the first time). Including my mess up, the whole process took about 10 minutes and now my iP1000 works perfectly!
Wow! I'm so happy! Thanks!! :guitar:

---

### Post by Amilius on 2007-05-12
I have a problem, I did every step as the thread says, and all seemed to go well, but the printer doesn't show as added on the printers control panel, when I try to do everything all over again, it tells me 

The PPD
	/usr/share/ppd/custom/canonpixmaip1000.ppd
is already installed

---

### Post by thorwood on 2007-05-12
ARRRG
I got my MP500 to work on my laptop, but on my Fedora run desktop it wont work!!!!
help okease

---

### Post by lobotomize on 2007-05-22
Awesomeness! TurboPrint was a joke (free version is justification to throw a 1/2 page ad on your document?)

I have a Canon PIXMA iP1700, and although there wasn't a driver for this model, the driver for the IP2200 worked well (as was mentioned on other websites). 

thanks again

---

### Post by Tehal on 2007-05-30
I am new to ubuntu and have the above printer..

I dont understand how to add the repository can someone explain how to do this


Thanks

---

### Post by MaroWitch on 2007-05-31
1. Write in terminal:
sudo vim /etc/apt/sources.list
2. navigate to the end of file
3. press "i"
4. write new repository
5. press "esc"
6. write ":wq"
7. sudo apt-get update
8)

---

### Post by sjh874 on 2007-06-04
I have the Pixma ip1700 and I've gotten as far as installing the packages but it gives me an error...

[COLOR="Blue"]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bjfilter-2.6: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
  pstocanonbj: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
               Depends: libcupsys2 (>= 1.2.3) but 1.2.0-0ubuntu5 is to be installed
E: Broken packages[/COLOR]


Is there possibly something I missed, or is there at least a way to fix it?

---

### Post by vladimirprieto on 2007-06-15
> **hamenarin said:**
> It works also on my Feisty Fawn Beta 3!
Thanks!

just say that also works on final 7.04.

thanks too.

---

### Post by lobotomize on 2007-06-18
[QUOTE=sjh874]Hey, I've been trying to get my printer to work and noticed that you had stated you got yours to. So if you have any pointers... the package for the 2200 isn't being found. I'm also on AIM "sjh874" if that would be a way for us to talk[/QUOTE]

Here's what I did to get it working:

from the terminal:

```
dperry@dperry-desktop:~$ sudo gedit /etc/apt/sources.list
```

then at the end of the file I inserted:

```
# Canon print package
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
```

next, from the terminal

```
dperry@dperry-desktop:~$ apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
```

Make sure to run ```
sudo apt-get update -f
``` to get any dependencies.

After this,  open System>Admin>Printing and click on New Printer.

Select "Detected Printer" and select "Canon iP1700".  Click "Forward".

From the list of models, select "iP2200 Ver.2.60". Click "Forward.

You can enter a description/name/location here.

Click Apply.

In the printers dialog, right click on the new Canon entry, properties, and try out a test page.

I uninstalled my printer to try this all out, and everything worked fine as I described. 

Hope this helps

---

### Post by grizzlysmit on 2007-06-22
Thank you this worked in ubuntu Feisty Fawn too now I have a working printer in linux

---

### Post by Candace on 2007-06-24
Help with Canon Pixma ip1700:

I followed the above method to get my canon pixma to print - and it works fine from tomboy notes, or text editor, and from web pages, but it will not print from open office, (edit) from the GUI or from the command line. I also cannot print pdf files.

I don't get error messages in open office - it says it is printing, but when I check the list of print jobs for my printer, the job never shows up that I sent from oo. 

Do I need another driver or something or does Canon just not support printing from certain programs, as I suspect? I didn't realize this when I bought my printer...

Thanks for any help.

---

### Post by TyPhoon101 on 2007-06-29
thanks ! i now have my canon printer working under ubuntu :D

---

### Post by sk8ron on 2007-07-01
> **MaroWitch said:**
> 1. Write in terminal:
sudo vim /etc/apt/sources.list
2. navigate to the end of file
3. press "i"
4. write new repository
5. press "esc"
6. write ":wq"
7. sudo apt-get update
8)

What does he mean when he says write new repository?

---

### Post by TyPhoon101 on 2007-07-02
he meant to add the line  			 				deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu]("http://mambo.kuhp.kyoto-u.ac.jp/%7Etakushi/ubuntu") ./ to your repository list .

---

### Post by ghiocel on 2007-08-04
Cool! My printer is now installed, after a week of efforts...but.. it prints blank pages. :( Any idea why it's doing this to me, right now when I need it so much??

---

### Post by canadian on 2007-08-23
I am running Xubuntu with the kde desktop and I added the debian repository "deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./' but when I run 
sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj I get an error message saying:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libcnbj-2.5

Any Ideas? Thanks in advance. :)

I am running an AMD 64 bit. Just bought it yesterday. :)

---

### Post by TyPhoon101 on 2007-08-23
did you type apt-get update after adding the repository ?

---

### Post by canadian on 2007-08-24
It seems that the  file source doesn't exist anymore .......

---

### Post by guhpraset on 2008-05-08
After upgraded to HH my pixma gone useless. So I tried tdh's DEB [here]("http://ubuntuforums.org/showthread.php?t=730598") and failed. Then i follow yours...

> The following NEW packages will be installed:
  bjfilter-2.5 libcnbj-2.5 pstocanonbj
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 6175kB of archives.
After this operation, 11.5MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  bjfilter-2.5 libcnbj-2.5 pstocanonbj
Install these packages without verification [y/N]? y
Get:1 [http://mambo.kuhp.kyoto-u.ac.jp](http://mambo.kuhp.kyoto-u.ac.jp) ./ bjfilter-2.5 1-1 [179kB]
Get:2 [http://mambo.kuhp.kyoto-u.ac.jp](http://mambo.kuhp.kyoto-u.ac.jp) ./ libcnbj-2.5 0-1 [5983kB]              
Get:3 [http://mambo.kuhp.kyoto-u.ac.jp](http://mambo.kuhp.kyoto-u.ac.jp) ./ pstocanonbj 3.3-1 [13.2kB]            
Fetched 6175kB in 16min17s (6320B/s)                                           
Selecting previously deselected package bjfilter-2.5.
(Reading database ... 98047 files and directories currently installed.)
Unpacking bjfilter-2.5 (from .../bjfilter-2.5_1-1_i386.deb) ...
Selecting previously deselected package libcnbj-2.5.
Unpacking libcnbj-2.5 (from .../libcnbj-2.5_0-1_i386.deb) ...
Selecting previously deselected package pstocanonbj.
Unpacking pstocanonbj (from .../pstocanonbj_3.3-1_i386.deb) ...
Setting up bjfilter-2.5 (1-1) ...
Setting up libcnbj-2.5 (0-1) ...

Setting up pstocanonbj (3.3-1) ...
 * Reloading Common Unix Printing System: cupsd                          [ OK ] 

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

then go to System > Administration > Printing

with the same setting from previous failed attempts (device uri: usb://Canon/iP1000 and make and model: Canon PIXMA iP1000 Ver.2.50) i click test page.

SUCCESS... but.. i stuck with 'letter' paper size. even i change from the printing menu, open office will stuck to 'letter'. So i have to change '/etc/papersize' to 'A4'. Weird.

Anyway, thank you very much. Now i can have better sleep.

Thank You!

---

### Post by johnny008 on 2008-07-03
I am Using UBUNTU 8.04 LTS. For the 1st time with Canon Pixma ip1000. I read your entire threads.But my printer isn't printing at all. PLZ HELP ME WITH STEP BY STEP PROCEDURE. otherwise, I MUST BACK TO WINDOWS XP. REPLY ME ONLY ON THIS MAIL ADDRESS:
[email]johnny_aust_eee@yahoo.com[/email]

---

