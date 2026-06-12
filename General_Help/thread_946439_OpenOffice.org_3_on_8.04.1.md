---
title: "OpenOffice.org 3 on 8.04.1"
date: 2008-10-13
forum: General Help
---

### Post by parampreet on 2008-10-13
I'm trying to install OpenOffice.org 3 on Hardy. Will the .deb available for download at OpenOffice.org replace the existing OpenOffice installation that comes preloaded on Hardy?
Secondly, when is OpenOffice.org 3 expected to be available in the Ubuntu repositories?

---

### Post by -Zeus- on 2008-10-13
well, for starters, it will probably be available when it actually gets released.

---

### Post by lykwydchykyn on 2008-10-13
That'd be today, -Zeus-.

I'd say check openoffice.org's site, but the probabilities of getting it to load are limited...  (servers must be running solaris)

---

### Post by howefield on 2008-10-13
> **parampreet said:**
> I'm trying to install OpenOffice.org 3 on Hardy. Will the .deb available for download at OpenOffice.org replace the existing OpenOffice installation that comes preloaded on Hardy?
Secondly, when is OpenOffice.org 3 expected to be available in the Ubuntu repositories?

The .deb is available at the openoffice website and will replace your existing installation.

---

### Post by howefield on 2008-10-13
The openoffice servers are indeed down, have been for about an hour.

---

### Post by Dai777 on 2008-10-13
I installed openoffice 3 and it works OK but, Im having troubled installing the menus for openoffice 3.

getting this error:
Error: Conflicts with the installed package openoffice-core

any ideas on how to solve this

---

### Post by GraveyardPC on 2008-10-13
> **Dai777 said:**
> I installed openoffice 3 and it works OK but, Im having troubled installing the menus for openoffice 3.

getting this error:
Error: Conflicts with the installed package openoffice-core

any ideas on how to solve this

```
sudo apt-get --purge remove openoffice.org-core
```

I'm waiting on a 64bit deb. The site is up and the downloads are working but they're all 32bit.

Edit: Never mind, found one at [http://openoffice.cs.utah.edu/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz](http://openoffice.cs.utah.edu/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz)

---

### Post by meho_r on 2008-10-13
> **GraveyardPC said:**
> 
I'm waiting on a 64bit deb. The site is up and the downloads are working but they're all 32bit.

Edit: Never mind, found one at [http://openoffice.cs.utah.edu/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz](http://openoffice.cs.utah.edu/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz)

Thanks for the link :)

---

### Post by soho2014 on 2008-10-13
I was able to install it - a real miracle, considering I had to install with the command line, and it works fine.

I just used the dpkg -i *.deb  command to install all the packages.  There is one more package for the menus outside of that deb package.  

Anyway, I like what I see.  They did a great job.

---

### Post by weirdtalk on 2008-10-13
> **soho2014 said:**
> 
I just used the dpkg -i *.deb  command to install all the packages.  

This is how I did it, but it didn't replace my 2.4 version.

I also had to run it by typing 

```

/opt/openoffice.org3/program/soffice

```

but otherwise it worked good.

---

### Post by stormtrooprdave on 2008-10-13
Will this be available through the update manager?  I found when I installed the oo3 beta I had openoffice 3 as well as 2.4 installed, causing confusion.  If i get a deb of the new oo3 will it overwrite 2.4?

---

### Post by saldarji on 2008-10-13
> **weirdtalk said:**
> This is how I did it, but it didn't replace my 2.4 version.

I also had to run it by typing 

```

/opt/openoffice.org3/program/soffice

```

but otherwise it worked good.

weirdtalk: try uninstalling the previous version of openoffice using:

```

sudo apt-get --purge remove openoffice.org-core

```

Then use dpkg -i to install the package in the folder desktop integration.  That'll provide you with the menu icons, etc.  Hope this helps.

---

### Post by russlar on 2008-10-13
> **GraveyardPC said:**
> I'm waiting on a 64bit deb. The site is up and the downloads are working but they're all 32bit.

Edit: Never mind, found one at [http://openoffice.cs.utah.edu/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz](http://openoffice.cs.utah.edu/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz)

The source is strong with this one.

---

### Post by mnk on 2008-10-13
Has anyone used it yet? How is it? 
How did you get it in the menu?

---

### Post by OutOfReach on 2008-10-13
I have it. It's pretty nice, but I've been using 3.0 since the BETA so I didn't really notice much of a difference.
I got it in my menu by making a shortcut that launches /opt/openoffice.org3/program/soffice
(In Openbox)

---

### Post by scouser73 on 2008-10-13
I followed this sites instructions; [http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/]("http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/") It's looking really good, especially the Start Centre, which I thought would have been made separate, but to access it you have to start Writer or one of the other modules then click close, then you see the Start Centre. But seeing as it's free I'm certainly not going to complain.

---

### Post by fballem on 2008-10-13
> **Dai777 said:**
> I installed openoffice 3 and it works OK but, Im having troubled installing the menus for openoffice 3.

getting this error:
Error: Conflicts with the installed package openoffice-core

any ideas on how to solve this

Completely uninstall OpenOffice 2 first

---

### Post by soho2014 on 2008-10-13
> **weirdtalk said:**
> This is how I did it, but it didn't replace my 2.4 version.

I also had to run it by typing 

```

/opt/openoffice.org3/program/soffice

```

but otherwise it worked good.

Oh, I should have mentioned that first I removed my old version with the Synaptic Package Manager just in case.:guitar:

---

### Post by GuitarRocker2562 on 2008-10-14
> **scouser73 said:**
> I followed this sites instructions; [http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/]("http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/") It's looking really good, especially the Start Centre, which I thought would have been made separate, but to access it you have to start Writer or one of the other modules then click close, then you see the Start Centre. But seeing as it's free I'm certainly not going to complain.

Ugh, there is like a general OpenOffice launcher that starts at the Start Center.

---

### Post by corydodt on 2008-10-14
I installed it from these debs and tried to open a docx file.

.docx files crash it, hard and fast. Then it attempts to recover the docx, which also crashes it. Not there yet, sorry.

---

### Post by kokkus on 2008-10-14
Hi.
I think I wanna try the 3.0 version but not sure yet.
It is still a beta and it seams to still have some bugs.
If I install it, what is better and what is worse with it?
Any new features or functions???

---

### Post by scouser73 on 2008-10-14
OpenOffice 3 has passed the beta staging hence it's general release as of yesterday 13/10/2008. To try the newer version you'll need to uninstall your existing OpenOffice. **sudo apt-get remove openoffice*.***

[http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/]("http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/")

****Notice****

I have stated that you need to uninstall the older version of OpenOffice before installing OO 3, this is not the case and I apologise for any confusion.

---

### Post by rasmith3530 on 2008-10-15
Noob issue here. Not sure if I messed this up or what. I downloaded and installed OOo 3.0 by unpacking the deb files and running "dpkg -i *.deb" from the directory containing the unpacked file. It went through and installed. I then read about uninstalling the 2.4 version, so I did that and went through the install routine again, as I still did not see any shortcuts to OOo applications in my Applications/Office menu.

Next, I tried running "/opt/openoffice.org3/program/soffice" and got an error message at the end, both in an Open Office 3.0 window and in terminal that "sunjavaplugin.so could not load Java runtime library" and it pointed to a truncated filename.

It sounds like this might be a path problem, but my Linux skills are still far too new to even begin to know how to correct this. Any assistance would be appreciated.

---

### Post by rasmith3530 on 2008-10-16
Thanks for the replies, but I got it figured out.

---

### Post by johnherron on 2008-11-08
> **rasmith3530 said:**
> Thanks for the replies, but I got it figured out.
I'm grappling with the same *"sunjavaplugin.so could not load Java runtime library"* you had run into about three weeks ago.

Now you've "got it figured out"; would you perhaps share with us how you managed to solve the problem? Thanks...

__________
johnherron

---

### Post by rasmith3530 on 2008-11-09
Sorry that I didn't post that John. I didn't invent the wheel here, just figured out how to mount it to the cart.  ;-)

First, I installed SUN Java from the repositories (Ubuntu by default uses a GNU version of Java that some applications don't like). You want to apt-get install sun-java6-jre. You will need to "sudo" to have permission to do this.

As mentioned, Ubuntu by default has a different flavor of Java installed, and it is the default. With Sun Java JRE installed, you still have to make it the default Java that applications see. To do this, there are two steps, both done at the CLI (if anyone knows how to do this in the GUI, please chime in). The two commands are as follows...

sudo update-java-alternatives -l 

This shows you what Java versions are installed.

sudo update-java-alternatives -s java-6-sun

This sets the default to the JRE version of Java.

Running "java -version" will show that you have the correct version installed as default.

As a side note, Firefox seems to like this as well.

---

### Post by samden on 2009-01-18
Same problem rasmith. Openoffice.org 3 won't start, lets me fill in my name etc in the dialogue it gives the first time you run it but crashes and returns:

[Java framework]sunjavaplugin.so could not load Java runtime library:

Tried following your instructions, but no change at all. No idea what the problem could be, very frustrating.

---

### Post by Pidgin on 2009-01-18
Add these sources:
For Intrepid:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```
For Hardy:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```
Then update the system. You will get the latest version of OpenOffice.org, which will replace the existing version.

---

### Post by jimbreslauer on 2009-01-20
Thanks for your post, Pidgin. Your instructions worked perfectly.

---

### Post by bixejo on 2009-01-23
> **Pidgin said:**
> Add these sources:
For Intrepid:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```For Hardy:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```Then update the system. You will get the latest version of OpenOffice.org, which will replace the existing version.
Thank you very much for this info, Pidgin.

Should we also install any keyring for this provider?

(I'd wish to officially thank you, but I don't know why I don't see the "thanks" button any more since some time ago. I don't see either anyone's "thanks" or "thanked" counter. Has this feature been removed from these forums?)

---

### Post by Lety on 2009-01-23
**bixejo**,
can't mark my thread as solved too,
[Thanks] and [Solved] options are temporary disabled because of some forum issues.

---

### Post by bixejo on 2009-01-23
> **Lety said:**
> **bixejo**,
can't mark my thread as solved too,
[Thanks] and [Solved] options are temporary disabled because of some forum issues.
Thank you for your info, Lety.

Let's wait till both [Thanks] and [Solved] get enabled again (I've got some thanks pending to be given, and also one thread I should mark as solved).

---

### Post by rasmith3530 on 2009-01-24
> **samden said:**
> Same problem rasmith. Openoffice.org 3 won't start, lets me fill in my name etc in the dialogue it gives the first time you run it but crashes and returns:

[Java framework]sunjavaplugin.so could not load Java runtime library:

Tried following your instructions, but no change at all. No idea what the problem could be, very frustrating.

Samden, I believe that your solution is fairly easy, but if you have a lot of Open Office customizations, you will lose them in the fix.

This assumes that you do have Sun Java installed and that it is your default Java install.

Run the following command...

rm -Rdf ~/.openoffice*

This should correct your problem and allow you to open Open Office 3.

---

### Post by rpremuz on 2009-03-15
> **bixejo said:**
> Thank you very much for this info, Pidgin.

Should we also install any keyring for this provider?

Yes, you should also add the authentication key for this repository from
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

-- rpr.

---

