---
title: "Skype Problems !!!"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by L.J on 2009-06-04
Hi, I am relatively new to linux and have been trying to make it my main operating system by installing some of my usual software, one of which is skype. I have been trying for the past couple of days to make this install work but i cannot seem to do it, my friend has installed it fine and will not help me do mine as he reackons i have to learn to deal with linux :-|. I have downloaded skype of their website and installing the package using synaptic package manager, evven tho it seems to of installed fine it, when i click the launcher (applications>internet>skype) a window appears with the heading "End User liscence Agreement", this only shows for a split second before exiting. Can anyone explain what is going wrong and what i can do to get skype up and running.

P.S. When i run it using terminal i get the message "Aborted" after the window has popped up once again. Hope this helps and i hope someone can help me. cheers

---

### Post by spcwingo on 2009-06-04
I would recommend uninstalling the version you currently have [also delete your profile (/home/yourusername/.Skype)] and enabling the medibuntu repository, if you haven't already.  Then:

```
sudo apt-get install skype-static
```

Instruction for enabling the medibuntu repo can be found here:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Let us know how it goes.  :)

---

### Post by L.J on 2009-06-06
hey thanks for the reply but i have just tryed the way you have explained and it hasnt worked, it did get me abit closer tho as i now have skype in the synaptic package manager, i have tryed to download this but it comes up with an error while installing and doesnt install. Any idea's ? all would be appreciated.

Cheers

---

### Post by spcwingo on 2009-06-06
When you run the code above, what error does it give (copy/paste the terminal output in your next post)?

---

### Post by L.J on 2009-06-06
i am unable to post the error as since my first post i have fully removed skype to try out you way of installing it. I cannot install it again as i keep getting an error message -> 

E: /var/cache/apt/archives/skype_2.0.0.72-1_i386.deb: trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common

Do you understand this ? What can i do to get past this and install skype again ?

Sorry for any inconvienice.

---

### Post by spcwingo on 2009-06-06
Try this code:

```
sudo apt-get clean && sudo apt-get autoclean && sudo apt-get install skype-static
```

This will clear the apt cache (old downloaded packages...although it will not uninstall the programs) and attempt to reinstall skype-static.  If you get any errors, please post them.

---

### Post by Ac1ds0ld13r on 2009-06-06
got the same issue with mine and jaunty

```

list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
--2009-06-06 14:27:26--  http://www.medibuntu.org/sources.list.d/jaunty.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 280 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 280         --.-K/s   in 0s      

2009-06-06 14:27:26 (14.3 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [280/280]

Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Hit http://wine.budgetdedicated.com jaunty Release.gpg
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_US
Get:1 http://packages.medibuntu.org jaunty Release.gpg [197B]
Ign http://packages.medibuntu.org jaunty/free Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Hit http://wine.budgetdedicated.com jaunty Release
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US
Get:2 http://packages.medibuntu.org jaunty Release [11.7kB]
Hit http://us.archive.ubuntu.com jaunty Release
Ign http://packages.medibuntu.org jaunty Release
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://security.ubuntu.com jaunty-security/main Packages
Ign http://wine.budgetdedicated.com jaunty/main Packages
Get:3 http://packages.medibuntu.org jaunty/free Packages [3258B]
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://wine.budgetdedicated.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Get:4 http://packages.medibuntu.org jaunty/non-free Packages [7943B]
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 23.1kB in 0s (28.3kB/s)
Reading package lists...
W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  libqt4-opengl dvgrab libqt4-assistant libqt4-test libwebkit-1.0-1
  libqt4-core xdotool vgrabbj libqt4-gui ftplib3 libtar libquicktime1
  libsdl-image1.2 libfaad0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 http://packages.medibuntu.org jaunty/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 0s (10.9kB/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 123894 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Hit http://wine.budgetdedicated.com jaunty Release.gpg
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Get:1 http://packages.medibuntu.org jaunty Release.gpg [197B]
Ign http://packages.medibuntu.org jaunty/free Translation-en_US
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Hit http://wine.budgetdedicated.com jaunty Release
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Get:2 http://packages.medibuntu.org jaunty Release [11.7kB]
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release
Ign http://wine.budgetdedicated.com jaunty/main Packages
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://packages.medibuntu.org jaunty/free Packages
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://wine.budgetdedicated.com jaunty/main Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://packages.medibuntu.org jaunty/non-free Packages
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 198B in 0s (233B/s)
Reading package lists...
ac1ds0ld13r@ac1ds0ld13r-desktop:~$ sudo apt-get install skype-static
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-opengl dvgrab libqt4-assistant libqt4-test libwebkit-1.0-1
  libqt4-core xdotool vgrabbj libqt4-gui ftplib3 libtar libquicktime1
  libsdl-image1.2 libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  skype-common
The following NEW packages will be installed:
  skype-common skype-static
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 22.0MB of archives.
After this operation, 27.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://packages.medibuntu.org jaunty/non-free skype-common 2.0.0.72-0medibuntu4 [2426kB]
Get:2 http://packages.medibuntu.org jaunty/non-free skype-static 2.0.0.72-0medibuntu4 [19.6MB]
Fetched 22.0MB in 19s (1115kB/s)                                               
Selecting previously deselected package skype-common.
(Reading database ... 123898 files and directories currently installed.)
Unpacking skype-common (from .../skype-common_2.0.0.72-0medibuntu4_all.deb) ...
Selecting previously deselected package skype-static.
Unpacking skype-static (from .../skype-static_2.0.0.72-0medibuntu4_i386.deb) ...
Processing triggers for man-db ...
Setting up skype-common (2.0.0.72-0medibuntu4) ...
Setting up skype-static (2.0.0.72-0medibuntu4) ...

```

Theres my output. It took a minute for me to do it correctly though so some of that is garbage.

In any event everything installed without a hitch that I can see.

---

### Post by L.J on 2009-06-06
I have so far gotten it to delete all the packages and reinstall them, once again just when i thought it would work, it hasn't... I ran it from terminal and got this->

lewis@lewis-desktop:~$ skype
Aborted
lewis@lewis-desktop:~$

Any help ?

---

### Post by merlinus on 2009-06-06
I have always downloaded the .deb file directly from the skype website and then used the GDebi package installer.  This is activated by right-clicking on the .deb and selecting that option.

Then it appears in Applications/Internet.

---

### Post by Ac1ds0ld13r on 2009-06-06
> **merlinus said:**
> I have always downloaded the .deb file directly from the skype website and then used the GDebi package installer.  This is activated by right-clicking on the .deb and selecting that option.

Then it appears in Applications/Internet.

Yeah, I know how to install it. The problem is that it's not working once its installed. And in the interim between this post and my previous post I've tried 3 other programs that claim to handle voip and all of them fail.

Which begs the question: Are there any programs out there that are easy to set up (I don't mind going into the terminal to hammer out a few lines of code here and there but I don't want to have to re-write the program either) and actually, you know.. WORK?

---

### Post by merlinus on 2009-06-06
Sorry, but the only things I can think of re: skype is that for some reason it did not load needed dependencies and/or detect your internet connection.

---

### Post by L.J on 2009-06-06
When it runs it shows the end user lisence agreement for a split second then aborts the operation, any knowledge on how to fix this as i think this is the main problem.

thanks.

---

### Post by L.J on 2009-06-08
Anyone have any knowledge on how to fix this as i cannot find a solution on the net yet :/.
Someone please help :-k

---

### Post by Ac1ds0ld13r on 2009-06-08
Not a fix, but it might save you some other headaches. 

I tried the Ekiga software, which seems to work fine, however it doesn't work at all with Skype. Skype uses a proprietary protocol, and from what I've seen, if it's not Skype, it won't work.

---

### Post by L.J on 2009-06-08
ok thanks, ill take a look and post what i find :)

cheers

---

### Post by L.J on 2009-06-08
oh and i have a question, does that software accept skype contacts or can it interact with skype users ?

cheers

---

### Post by Ac1ds0ld13r on 2009-06-09
No. Skype has a proprietary protocol. So if you want to do anything with your Skype contacts you need Skype. Sad story. :(

---

### Post by L.J on 2009-06-10
hmm well i need to get my skype working then :/, anyone now anything at all about my problem ?? If soo HELPPPPP !! :(

---

