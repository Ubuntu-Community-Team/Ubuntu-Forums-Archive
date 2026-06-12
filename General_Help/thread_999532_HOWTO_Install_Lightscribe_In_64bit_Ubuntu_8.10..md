---
title: "HOWTO: Install Lightscribe In 64bit Ubuntu 8.10."
date: 2008-12-02
forum: General Help
---

### Post by cchester on 2008-12-02
How to setup lightscribe host software and applications on 64bit Ubuntu 9.04.

The following instructions worked for me to install the Lightscribe Host software and applications under 64-bit Ubuntu 9.04. I want to thank all of those who have previously posted info on how to do this. This howto comes from various bits and pieces I found in getting this to install and work on my system.

First add the following packages if they're not already present through either sudo apt-get install <name of package> change this to the name of the package you wish to install or through synaptic package manager :

ia32-libs (Don't know if this is still needed since I converted the files to 64bit. So it is uo to you to install or not to install.)

Now you can move on to the next steps.

1.)Download the attached deb file below "lightscribe-1.18.6.1-linux-2.6-amd64.deb" it is the Lightscribe Host Software you will need to install this first. Just save it into your home directory. You can then double click on it later and install it just like any other deb file. (As of July 31, 2009 this was the most current version of the software.)

2.)For now all you need is to grab the icon below that you can use for later with your new applications. For now you can save the icon to your home directory.

3.)Now you can move on to install the Lightscribe Host Software. Just double click on the file you downloaded and GDebi should install it for you hopefully without errors.

4.)Open a terminal and copy and paste the following commands. (The following commands will resolve issues with referencing a required library.)

5.) sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib64/

6.) sudo ln -s /usr/lib/liblightscribe.so /usr/lib64/

7.) sudo ldconfig

Now you will notice that there are no entries on the desktop or the menu for your new programs. We will now create those as well. First we will start by putting the Lightscribe icon you downloaded somewhere that you can use it.

From a terminal window make sure the icon you downloaded is in your home directory and copy and paste the following command without the quotes "sudo cp lightscribe.png /usr/share/pixmaps/". (This will enable you to use the icon later for the Lightscribe Labeling Software.)

Here are links to RapidShare where I am hosting files that I converted to 64bit for the the Lightscribe Simple Labeler and the Lacie Labeler.

[http://rapidshare.com/files/262033121/4l_1.0-r6_amd64.deb.html]("http://rapidshare.com/files/262033121/4l_1.0-r6_amd64.deb.html")

[http://rapidshare.com/files/262033122/lightscribeApplications-1.18.6.1-linux-2.6-amd64.deb.html]("http://rapidshare.com/files/262033122/lightscribeApplications-1.18.6.1-linux-2.6-amd64.deb.html")

---

### Post by swatsbiz on 2009-05-22
> david@david-desktop:~/Desktop$ sudo dpkg -i --force architecture lightscribeApplications-1.10.19.1-linux-2.6-intel.deb
dpkg-deb: --control lightscribeApplications-1.10.19.1-linux-2.6-intel.deb /var/lib/dpkg/tmp.ci
(Reading database ... 158512 files and directories currently installed.)
Unpacking lightscribeapplications (from lightscribeApplications-1.10.19.1-linux-2.6-intel.deb) ...
dpkg-deb: --fsys-tarfile lightscribeApplications-1.10.19.1-linux-2.6-intel.deb
cp: cannot stat `lightscribeApplications-1.10.19.1-linux-2.6-intel.deb': No such file or directory
cd: 52: can't cd to debian/*/
dpkg: error processing lightscribeApplications-1.10.19.1-linux-2.6-intel.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
Errors were encountered while processing:
 lightscribeApplications-1.10.19.1-linux-2.6-intel.deb


What's going on here?

I've tried downloading the file several times but to no avail, any help would be appreciated.

David

---

### Post by cchester on 2009-05-22
Hello,

Which file are you trying to download? If the file is for the png file then I can't help because it was a link to a site that no longer seems to be there.

Did everything else work when you tried it? Like I said I just checked and all the links work when I click on them except the one for the png file.

Let me know.

---

### Post by swatsbiz on 2009-05-23
Yes the downloads worked fine, as you can see it's when I go to install the lightscribeApplications and the 4l_1.0-r6_i386.deb file that I get this error as posted above:

> dpkg-deb: --fsys-tarfile lightscribeApplications-1.10.19.1-linux-2.6-intel.deb
cp: cannot stat `lightscribeApplications-1.10.19.1-linux-2.6-intel.deb': No such file or directory
cd: 52: can't cd to debian/*/

Not sure why it can't make that directory

---

### Post by cchester on 2009-05-23
Hello,

I just downloaded the file again and ran the same command as before and I don't get the error and it installs fine.

Are you running the command from where you have the file?

I just have the file in my home directory and execute the command in the terminal from there using sudo and everything is fine.

I am doing this in Ubuntu 9.04 64bit so I am not sure as what to suggest other than what I have posted because it has always just worked for me with no problems.

Did you get all the previous dependencies and did they install correctly too? That would be the only other thing I could think of.

Let me know.

---

### Post by egalvan on 2009-05-23
> **cchester said:**
> ...
Idownloaded the file again and ran the same command as before and I don't get the error and it installs fine.


I am doing this in[COLOR="Red"]** Ubuntu 9.04 64bit**[/COLOR] so I am not sure as what to suggest other than what I have posted because it has always just worked for me with no problems.

Did you get all the previous dependencies and did they install correctly too? That would be the only other thing I could think of.


The title states "Ubuntu 8.10"

is this working for 9.04 64bit?

---

### Post by swatsbiz on 2009-05-24
> **cchester said:**
> 
Are you running the command from where you have the file?

I just have the file in my home directory and execute the command in the terminal from there using sudo and everything is fine.

I am doing this in Ubuntu 9.04 64bit so I am not sure as what to suggest other than what I have posted because it has always just worked for me with no problems.

Did you get all the previous dependencies and did they install correctly too? That would be the only other thing I could think of.

Let me know.

Yes I'm running the file from where it is saved, as you can see it accesses the file and starts the process, it's the next step that it falls down on :-(  I'm also using 64bit Jaunty ... as for dependencies, I'm not sure, but I have run through the above HOWTO word for word ...

David

---

### Post by cchester on 2009-05-24
Yep works great and fine in 9.04 64bit. I am using it now.

---

### Post by cchester on 2009-05-24
I am not sure then. I have had no problems with install it and running it. The only other thing I could think of is change the permissions. Chmod 777 the file or directory I think is what you would have to do.

Maybe someone else can chime in about permissons and write access and what to do since that seems to be the problem.

Sorry I can't be more help.

---

### Post by sickofthesea on 2009-05-25
swatzbiz, you're not going mad. Different software but same errors here. I'm trying to install the amazonmp3.deb, the Amazon UK MP3 downloader together with getlibs ([http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)). The downloader is i386 and I'm using 64bit jaunty.

collins@collins-laptop:~/Downloads$ sudo dpkg -i --force-architecture amazonmp3.deb 
dpkg-deb: --control amazonmp3.deb /var/lib/dpkg/tmp.ci
(Reading database ... 242349 files and directories currently installed.)
Unpacking amazonmp3 (from amazonmp3.deb) ...
dpkg-deb: --fsys-tarfile amazonmp3.deb
cp: cannot stat `amazonmp3.deb': No such file or directory
cd: 52: can't cd to debian/*/
dpkg: error processing amazonmp3.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
Errors were encountered while processing:
 amazonmp3.deb

I've downloaded this file again and again. It can't be corrupted a dozen times, can it? Either the files on the server are corrupt or there is a bug (or feature) on 9.04 that's not present in 8.10. But what software is causing the bug? I'm at a loss!!

Rgds,

Martin

---

### Post by brucewestfall on 2009-07-22
Getting the same message when trying to install print driver for a Brother multifunction printer.

> bruce@Brutus:~/Desktop$ sudo dpkg  -i  --force-all  --force-architecture mfc665cwlpr-1.0.1-1.i386.deb 
dpkg-deb: --control mfc665cwlpr-1.0.1-1.i386.deb /var/lib/dpkg/tmp.ci
(Reading database ... 142548 files and directories currently installed.)
Unpacking mfc665cwlpr (from mfc665cwlpr-1.0.1-1.i386.deb) ...
dpkg-deb: --fsys-tarfile mfc665cwlpr-1.0.1-1.i386.deb
cp: cannot stat `mfc665cwlpr-1.0.1-1.i386.deb': No such file or directory
cd: 52: can't cd to debian/*/
dpkg: error processing mfc665cwlpr-1.0.1-1.i386.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
Errors were encountered while processing:
 mfc665cwlpr-1.0.1-1.i386.deb

Also running 64 bit 9.04

Any thoughts as to why different packages are doing the same thing??

This exact same thing worked fine on 8.10.  Follow the instructions on the Brother site and the install goes fine.  Something is definitely wrong and it's not with the downloaded file.

---

### Post by slightlystoopid on 2009-08-26
has anyone found a resolution?

another example of the problem: [http://ubuntuforums.org/showthread.php?p=7847583#post7847583](http://ubuntuforums.org/showthread.php?p=7847583#post7847583)

---

### Post by cchester on 2009-08-26
I changed the instructions and created 64bit files. Have you tried them yet to see if it works?

Thanks.

> **slightlystoopid said:**
> has anyone found a resolution?

another example of the problem: [http://ubuntuforums.org/showthread.php?p=7847583#post7847583](http://ubuntuforums.org/showthread.php?p=7847583#post7847583)

---

### Post by onortosu on 2009-08-29
I'm having the same issue with amazonmp3.deb (MP3 downloader from amazon.com) and bibblelite_4.10.1-1_i386.deb (Photo editing tool from bibblelabs.com). These same files worked on 8.10 for me, but apparently they're not working in 9.04. I don't know if it's some mix of libraries that's screwing this up.

Has anyone had any luck?

Thanks

---

### Post by cchester on 2009-08-30
Hello,

Are you trying to install these in Ubuntu 64 bit? If so post the files and I will try and convert them to 64bit and see if that helps. Might help if you start a new thread though since I started this thread to help people install Lightscribe in Ubuntu 64bit.

Let me know.

> **onortosu said:**
> I'm having the same issue with amazonmp3.deb (MP3 downloader from amazon.com) and bibblelite_4.10.1-1_i386.deb (Photo editing tool from bibblelabs.com). These same files worked on 8.10 for me, but apparently they're not working in 9.04. I don't know if it's some mix of libraries that's screwing this up.

Has anyone had any luck?

Thanks

---

### Post by keithwwalker on 2013-03-22
The download for the 64 bit LaCie labeler software is down, do you still have a copy?  It would save me a bit of work if you did!

---

### Post by oldos2er on 2013-03-22
Old thread closed.

---

