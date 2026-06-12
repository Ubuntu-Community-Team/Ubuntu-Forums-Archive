---
title: "Install Picasa on Dell Mini 9"
date: 2008-11-17
forum: Hardware
---

### Post by GJRick on 2008-11-17
I helped setup a little Dell Mini 9 today with Ubuntu, but could not install Picasa 3 or 2.7 from the .deb files because of an error saying "wrong architecture". I tried the 32 bit and 64 bit i386 downloads.

Any ideas on getting it successfully installed would be greatly appreciated. Thanks.

---

### Post by pytheas22 on 2008-11-17
You might have better luck if you try installing the packages from the command line, which you would do by typing:
```

sudo dpkg --install package-name.deb
```

(Obviously, replace 'package-name' with the name of the .deb file.)  If that fails and you're sure that you're using the package built for the right architecture, please post here all of the output that you get.

Also, as I recall, the 'Linux' version of Picasa is just the Windows version packaged up with wine, since Google apparently doesn't want to be bothered to compile a real native Linux version.  So as an alternative to the above, you could basically install the same thing by first installing wine:
```

sudo apt-get install wine
```

and then downloading the Windows .exe file for Picasa and opening it.

---

### Post by GJRick on 2008-11-18
Thanks pytheas. However, I have tried the command line option and still get the wrong architecture error. And to my knowledge, the latest versions of Picasa 2.7 and 3 are native Linux apps...and do not require Wine. Also, for this little netbook with the Atom processor, the less I have on the machine the better...I really just want to get the Picasa to work the way it does on any other Ubuntu install I've done. 

I keep trying to bring clients over to Ubuntu/Linux, but hurdles like these make it hard for me to keep them excited over all the positives of Ubuntu because they can't get past these stumbling blocks.

---

### Post by pytheas22 on 2008-11-18
You can use the --force-architecture argument with 'dpkg' to get it to install even if it thinks the architecture is wrong.

I'm also reading that Google has set up repositories for installing Picasa.  Have you tried adding Google's repository to your /etc/apt/sources.list file, as per [these instructions]("http://www.google.com/linuxrepositories/testrepo.html")?  That may work better than trying to download the individual packages.  You're supposed to be able to do it easily by typing:
```

wget https://dl-ssl.google.com/linux/google-repo-setup.sh
bash google-repo-setup.sh
```

Finally, it seems that Picasa 3 is still just the Windows version packaged with wine, since it says on the [Picasa site]("http://picasa.google.com/linux/download.html#picasa30"):
> 
All downloads are approximately 30 MB: Picasa software (13 MB), Wine (11 MB) and Gecko engine (6 MB). 

So there's probably no way to get around using wine, and installing using the Windows package would give you the same software.  Also, since you're worried about wasting resources, keep in mind that wine isn't any less efficient than running something natively; it's an application compatibility layer, not a hardware emulator, and doesn't waste system resources trying to do binary emulation.

> 
I keep trying to bring clients over to Ubuntu/Linux, but hurdles like these make it hard for me to keep them excited over all the positives of Ubuntu because they can't get past these stumbling blocks.

In Ubuntu's defense, I would point out that if Google acted on its ostensible commitment to Free software by releasing the Picasa source so that Ubuntu could include it in its standard repositories and people outside of Google could fix problems with the packages, it's likely that the problem you're having would have been resolved long ago.  But I understand that most normal people don't know what any of this means and are just frustrated when things on Linux don't work, even if they're beyond the control of the free-software community.

---

### Post by GJRick on 2008-11-19
Thanks again pytheas22...I will give that a try later this week or early next when I see my customer again and report back for other users as well. 

And thanks also for the explanation of how programs make it into the Ubuntu repositories. I need to keep learning about Ubuntu/Linux myself and appreciate the information. I started using and learning Ubuntu for the first time just less than 2 years ago and find that it meets the needs of a larger majority of computer users IF they can open their minds just a little.

---

### Post by GJRick on 2008-11-21
Update. I added the Google repositories and still had no success. Here's a copy of what I'm experiencing with this little Dell netbook. Does this help? Thanks.

acknmarilyn@jacknmarilyn:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1300B]
Get:4 [http://dl.google.com](http://dl.google.com) testing Release [772B]
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Fetched 2450B in 2s (936B/s)
W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  non-free/binary-lpia/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://dl.google.com/linux/deb/dists/testing/Release](http://dl.google.com/linux/deb/dists/testing/Release)  Unable to find expected entry  non-free/binary-lpia/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
jacknmarilyn@jacknmarilyn:~$ sudo apt-get install picasa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package picasa
jacknmarilyn@jacknmarilyn:~$

---

### Post by pytheas22 on 2008-11-21
That's weird...

What does your /etc/apt/sources.list file look like?

It also wouldn't hurt to see all the output you get if you try to install Picasa in the terminal using a command like 'dpkg --install picasa-i386.deb'.

And you're not having problems installing any other packages, right?

---

### Post by GJRick on 2008-12-09
I finally got that little Dell Mini back in my hands and was able to install Picasa 3 by doing the following:

[LIST=1]
[*]I downloaded the latest version (currently 3 Beta) of Picasa from:
[*][http://picasa.google.com/linux/](http://picasa.google.com/linux/)
[*]renamed the file to picasa.deb to make it easier in the terminal
[*]Start a Terminal session
[*]Change to the directory where the download is saved
[*]Type:  ```
sudo dpkg --install --force-architecture picasa.deb
``` (or name of your file)
[*]Answer yes to any questions that might come up during the install
[/LIST]

That did it! Thanks to pytheas22 for his guidance and a combined tip about the force architecture thing from a Dell forum. You DO NOT need Wine to run Picasa...Google has created a good product that is a native Linux app. I hope this helps a few others as well.

---

