---
title: "How to Install Adobe Acrobat Reader 9.1"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2009-03-29
When I go to the Adobe website to download Adobe Acrobat Reader 9.1 it recognizes that I am running Linux, but the file that it delivers to me has a .bin extension, and I am unable to open it or execute it.

What am I supposed to do with this file?

Once I have Reader installed, how do I activate the Firefox plugin?

---

### Post by oldos2er on 2009-03-29
Assuming the *.bin is on your desktop, open a terminal and run these commands one at a time:
```
cd Desktop
chmod a+x *.bin
sudo ./*.bin
```
 Replace the * with whatever the file name is.

---

### Post by William Anderson on 2009-04-08
you can also download a DEB file from the Adobe web site. Follow the "Different language or operating system?" link, select "Linux - x86 (.deb)" from the "Select an operating system" drop down list box, choose your language and press Continue. This brings up Step 2 of 2 where you select the version to download. 
 
If you save the file, run the command "sudo dpkg -i package_file.deb" where the string package_file.deb is replaced with the Adobe Reader deb file. 

This way the software package manager will know about the Adobe Reader and can be used to update or remove it in the future.

Hope this helps,

William

---

### Post by TimDaniels on 2009-04-18
> **William Anderson said:**
> you can also download a DEB file from the Adobe web site. Follow the "Different language or operating system?" link, select "Linux - x86 (.deb)" from the "Select an operating system" drop down list box [...]

Thank - YOU!  I had the same problem for several days, and that solved it!  I guess I didn't see the scroll bar, and I didn't scroll down to the ".deb" selection.

*TimDaniels*

---

### Post by fox mulder on 2009-04-19
Ive followed these instructions and get this error message
E: /var/cache/apt/archives/acroread_9.1.0-7intrepid1_i386.deb: trying to overwrite `/usr/share/man/man1/acroread.1.gz', which is also in package acroread-debian-files
any help would be appreciated

---

### Post by 45acp on 2009-04-19
I am wondering about this also. I get the same error when installing updates with the update manager.

---

### Post by Mishal on 2009-04-19
Same problem here. Someone please help.

---

### Post by krgp on 2009-04-20
I get the same error, and have the update manager icon always telling me that adobe reader needs updating.

---

### Post by William Anderson on 2009-04-24
Hi,

You have already installed the ubuntu supplied acroread package. The error is because the Adobe package is trying to overwrite a file in that already installed package.

There are two ways to fix this: force the package manager to ignore this kind of error, or remove the Ubuntu acroread package. The first is dangerous because a future upgrade might break things in unpredictable and hard to diagnose ways (ie a new library with a different interface causes one package to fail after the other is upgraded.)

To remove the Ubuntu acroread package, use synapatic, search for acroread, click on the green check box and select "Mark for removal". Next click on the Apply button in the toolbar and follow the prompts. From the command line you can run "sudo apt-get remove acroread".

Both of these processes should prompt for the removal of any packages, such as the firefox plugin, if they are installed. You will need to remove these packages as well. 

Once the Ubuntu acroread package is removed, you can then install the Adobe package. 

Hope this helps,

William

---

### Post by Giguntu on 2009-04-26
Is there also a way to install Adobe with apt-get or similar package manager???

---

### Post by 600WPMPO on 2009-05-01
> **William Anderson said:**
> Hi,

You have already installed the ubuntu supplied acroread package. The error is because the Adobe package is trying to overwrite a file in that already installed package.

There are two ways to fix this: force the package manager to ignore this kind of error, or remove the Ubuntu acroread package. The first is dangerous because a future upgrade might break things in unpredictable and hard to diagnose ways (ie a new library with a different interface causes one package to fail after the other is upgraded.)

To remove the Ubuntu acroread package, use synapatic, search for acroread, click on the green check box and select "Mark for removal". Next click on the Apply button in the toolbar and follow the prompts. From the command line you can run "sudo apt-get remove acroread".

Both of these processes should prompt for the removal of any packages, such as the firefox plugin, if they are installed. You will need to remove these packages as well. 

Once the Ubuntu acroread package is removed, you can then install the Adobe package. 

Hope this helps,

William

I was wondering if I can do it more simply, you know, all this installing a .deb file & then removing acroread...

Here's how:

1. Open Synaptic
2. Search for acroread
3. Mark & install

Would this be any different from installing from adobe's site ? 

p.s. I have alredy downloaded the 60 MB .deb file from adobe, but I would like to install in the way I mentioned above. Am I doing right ? :confused:

---

### Post by bngguy on 2009-05-01
> **600WPMPO said:**
> I was wondering if I can do it more simply, you know, all this installing a .deb file & then removing acroread...

Here's how:

1. Open Synaptic
2. Search for acroread
3. Mark & install

Would this be any different from installing from adobe's site ? 

p.s. I have alredy downloaded the 60 MB .deb file from adobe, but I would like to install in the way I mentioned above. Am I doing right ? :confused:

Yes you are doing it right, just delete the file you downloaded from adobe, synaptic will download from the ubuntu archive and install adobe 9.1

---

### Post by 600WPMPO on 2009-05-01
yessir, I installed it via synaptic.. as easy as it can be..!! :P

---

### Post by koshari on 2009-05-09
in 9.04 i cant find any acroread in the repos except for the amd64 build, 

i downloaded the bin file anyway and put it in my path , ran the installer and installed it to my home dir, without root permissiona and its seems to work anyway,

---

### Post by karlson on 2009-10-14
I've just looked over the medibuntu.org package repository and acroread is missing from repositories for all versions.

Is there a problem with the package?

Does anyone know when it will become available if ever?

---

### Post by projectbronco on 2009-10-16
I tried installing the .deb file and got:
Errors were encountered while processing:
 AdbeRdr9.1.2-1_i386linux_enu.deb

So I double clicked on the file and the package manager said:
Status: Error: Wrong architecture 'i386'

Is this because I have the 64 bit system. Also, I'm still running 8.10...
Thanks for any help.

---

### Post by kostkon on 2009-10-16
> **karlson said:**
> I've just looked over the medibuntu.org package repository and acroread is missing from repositories for all versions.

Is there a problem with the package?

Does anyone know when it will become available if ever?
I think now is offered by the Partner repo so you can easily install it in Ubuntu without the need to add the Medibuntu repo.

---

### Post by phillw on 2009-10-16
Soz, I cannot remember how i linked things up for adobe reader ...

acroread is in the repository (Synaptic Package Manager)

But, I didn't use that ... from memory it was along these lines ..

[http://ubuntuguide.net/install-adobe-reader-on-ubuntu-904](http://ubuntuguide.net/install-adobe-reader-on-ubuntu-904)

My updates for reader & flash install when there is a new update. 
Adobe is, actually, *nix friendly - You do, however, have to tell the down-load section
what it is you want - in the case of ubuntu (which is listed) - you need the deb section - or, at least you did when I was doing my initial install.

You may need alien (Synaptic Package Manager)

For it to easily install.

I've no doubt others will say of other ways - All I say is what works for me :P

Phill.

---

### Post by izak on 2009-10-30
How do you get this installed on 64 bit? 

acroread is not in the standard repository. 
All the binaries/debs available from adobe's site are __x86.

> But, I didn't use that ... from memory it was along these lines ..

[http://ubuntuguide.net/install-adobe...-on-ubuntu-904](http://ubuntuguide.net/install-adobe...-on-ubuntu-904)

I also tried to follow the above help but acroread is apparently not in the medibuntu 64 bit repository eiter.

Any help please?

---

### Post by izak on 2009-10-30
After searching some more, I [found out that]("http://ubuntuforums.org/showthread.php?t=1161163") one must ad canonical partners to the repository, not medibuntu. This worked for me on jaunty 64 bit.

---

### Post by faical117 on 2009-10-30
_Step 1_: Add the Medibuntu repository. 
Run the following command in a terminal 

-> echo deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free | sudo tee -a /etc/apt/sources.list

_Step 2_: Install the appropriate keys and update the software sources list. (Do not worry if this step fails)

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add &#8211; && sudo aptitude update

Step 3: Search and install whatever you like. 

sudo apt-get install acroread mozilla-acroread acroread-plugins

:KS

---

### Post by NormanFLinux on 2009-10-30
Majing things easier on yourself and choose other operating systems from the Adobe menu and chose Linux X86 (deb.) It will download a Debian package file that can be installed with the Gdebi installer.

---

