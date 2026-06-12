---
title: "OpenOffice 2.4 to 3.0"
date: 2008-11-30
forum: General Help
---

### Post by Telhma on 2008-11-30
Hello, i found out i still have OpenOffice 2.4 on my system, i went to "add & del programs tool to update it to 3.0. But it looks like it is not possible there.

can somebody tell me how I can update to 3.0 ??

thanks

---

### Post by TeXtonyx on 2008-11-30
[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)
First, remove your existing version of OpenOffice.org:

sudo apt-get remove openoffice*.*
steps ...

With that done you should have just one thing left to do: Install the
desktop integration package. That should be in the DEBS folder:

cd desktop-integration

From that folder install the package:

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

I've read that sudo dpkg -i -R may be a better syntax.

Her is another website that makes a similar recommendation,

-------------------------------

[http://www.rebelzero.com/ubuntu/inst...hardy-heron/27](http://www.rebelzero.com/ubuntu/inst...hardy-heron/27)

[http://www.rebelzero.com/ubuntu/](http://www.rebelzero.com/ubuntu/) [copy and paste into one line]
installing-ooo-300-onto-hardy-heron/27


"If you already have OpenOffice.org 2.4.1 installed through Ubuntu&#8217;s
repos, you will need to remove it. One of the 3.0.0 packages (debian
menus) has a conflict with one of the 2.4.1 packages,
openoffice.org-core. Removing openoffice.org-core will also remove OO.o
2.4.1 from your computer. Remove OO.o 2.4.1 by using apt-get at the
command line:

sudo apt-get remove openoffice.org-core

You&#8217;ll see apt-get prompt you for removing the other 2.4.1 packages as well.
Just hit enter and apt-get will do the rest. Proceed to Step 3b.

-------------------------------------------------

---

### Post by fragos on 2008-11-30
The simple way is to enable backports in the Software Sources Updates tab.

---

### Post by binbash on 2008-11-30
> **fragos said:**
> The simple way is to enable backports in the Software Sources Updates tab.

There are no pkgs there.

---

### Post by Beernut on 2008-11-30
> **binbash said:**
> There are no pkgs there.

They were removed due to a bug.  I have been waiting for the fixed packages myself.

---

### Post by binbash on 2008-11-30
> **Beernut said:**
> They were removed due to a bug.  I have been waiting for the fixed packages myself.

AS far as i know it is not going to fix for intrepid or hardy

---

### Post by exploder on 2008-11-30
I prefer the deb packages from Sun. Why wait and wonder if OO 3 will be available for Hardy and Intrepid? The version provided by Sun provides the ability to update out of the box. I will use the official packages from Sun any day over what is in the Ubuntu repos. Every other major distribution has OO 3 by default.

---

### Post by wjp.reg on 2008-11-30
Another issue (for me anyway) is that the ubuntu version of openoffice has limited support for address data sources (pretty much imited to Evolution).  The versions from Sun supports  Thunderbird, LDAP, Groupwise, in addition to Evolution, and I like to use Thunderbird which is available across OS platforms.

cheers!

---

### Post by exploder on 2008-11-30
This guide is complete and accurate.

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

I have installed OpenOffice 3 in Hardy, Intrepid and Mint 5 using this guide with no problems. wjp.reg brings up another good point for using the Sun packages.

---

### Post by Arup on 2008-11-30
The backport is gone for now, they have announced they will only support Ubuntu 9x Jalopy and there won't be any version for Intrepid or Hardy. The OO debs is the only way to install, it works fine except unlike the backport version, this one has no quickstarter.

---

### Post by Beernut on 2008-11-30
Well since hearing that it's not going to be fixed I just installed the OpenOffice version using this [forum thread]("http://ubuntuforums.org/showthread.php?p=5966220") without any problems.  The new version starts much quicker without any quickstart.

PS: I installed the 64 bit version.

---

### Post by Skripka on 2008-11-30
> **Arup said:**
> The backport is gone for now, they have announced they will only support Ubuntu 9x Jalopy and there won't be any version for Intrepid or Hardy..

Where have you read or heard this?

---

### Post by Arup on 2008-11-30
> **Skripka said:**
> Where have you read or heard this?


[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

Check Ed Jolanski's response in the bottom.

---

### Post by Skripka on 2008-11-30
> **Arup said:**
> [http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

Check Ed Jolanski's response in the bottom.

Hm.  I have no clue who Ed Jolanski is...is he somehow on the inside of all this?...all I know is the Jaunty repos are just as empty as the Hardy and Ibex repos---and the banner on the repo page says:

 "OpenOffice.org 3.0.0 - INTREPID/JAUNTY ONLY

The packages were buggy and crashed when openoffice.org-gnome was installed, they will be reuploaded when the bug has been resolved."

:confused:

---

### Post by Arup on 2008-11-30
He is just quoting one of the guys who run that launchpad. Actually even though the quickstart is missing from the regular version of OO3, I find the method of removing the Ubuntu OO and installing OO3 via downloaded deb to be a better method.

---

### Post by fragos on 2008-11-30
> **Beernut said:**
> They were removed due to a bug.  I have been waiting for the fixed packages myself.

I got them from backports before they were removed but haven't run accross any bugs yet. Most of my use is of Writer, perhaps it's more stable.

---

### Post by Arup on 2008-12-01
> **fragos said:**
> I got them from backports before they were removed but haven't run accross any bugs yet. Most of my use is of Writer, perhaps it's more stable.

Its the gnome-open office update from Ubuntu that killed the backport OO3 package, the Sun deb package is unaffected by it.

---

### Post by zika on 2008-12-01
I've installed OpenOffice 3 through repos. After update several days ago, among many other, my OO3 went missing in action. It dissappeared from menus and it can not be started. I tried packages from several places and istall goes OK but with no effect. Office won't start. I was waiting for repos to come on-line again. Now that I read that they won't I will have to try to go back to OO2.4 from Intrepid. But when I try that I get:

> This application conflicts with other installed software. To install 'openoffice.org' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

Is there reliable way to go back to OO2.4?

I am a heavy TeX user and Office is just for crossover purposes ...

---

### Post by Arup on 2008-12-01
You can remove OO3 via synaptics and then install OO2.4 but I would suggest you remove both and install OO3 from the Sun debs. Works quite well.

---

### Post by Pellervo Kässi on 2008-12-01
As Arup said, you can install the OO 2.4 through synaptic (or apt). You can also install the Sun's debs without removing the 2.4 if you don't install the debian-menus, package. In this case you just need to make own launcher's for OO3. OO3 is installed in /opt/openffice.org3 and the ubuntu 2.4 is installed in /opt/openffice.org3 .

---

### Post by zika on 2008-12-01
I've done the following:

```
sudo apt-get remove openoffice*.*
```After that I've installed OpenOffice.org Suite through Add/Remove (is that Aptitude or Synaptic?).

Now I have OpenOffice again and, probably, OO3 will wait until JJ.

Thank You all!

(In one of these forums a gyu attacked all of us that were inpatient by saying that an application is always a part of OS. I do not completely agree with him but now I am a bit closer ... Nevertheless, I learned a lot from tinkering with this these several days (27.11. to 01.12) ;)

---

### Post by Beernut on 2008-12-01
> **zika said:**
> 
(In one of these forums a gyu attacked all of us that were inpatient by saying that an application is always a part of OS. I do not completely agree with him but now I am a bit closer ... Nevertheless, I learned a lot from tinkering with this these several days (27.11. to 01.12) ;)

That's ridiculous an application shouldn't be part of the OS.  The OS should do it's job and Operate the System in my opinion that's the problem with windoze.

I was in a hurry for version 3 because I really needed the PDF import extension.

Glad you got 2.4 working again.

---

### Post by joeljoseph999 on 2009-12-30
Hi 
 Itried uninstalling the existing version of Openoffice but im getting the following error.

Do you want to continue [Y/n]? Y           
(Reading database ... 117886 files and directories currently installed.)
Removing openoffice.org-hyphenation-en-us ...
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm: 6: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-hyphenation-en-us (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 openoffice.org-hyphenation-en-us
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can u pls guide me since im new to Linux
Regards
Joel

---

