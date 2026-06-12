---
title: "ubuntu intrepid ibex ubdate problem"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Santooka on 2009-01-30
Dear all,

it has been 13 days now since my last ubuntu daily updates...

and that's because each time the automatic update checks for any new updates he gets this:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CA1F91146F087E5A
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5DC4E17435661D98
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24C
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FE8956A73C5EE1C9
W: Failed to fetch http://nightlies.videolan.org/build/intrepid-i386/arch/./Release.gpg  Could not connect to nightlies.videolan.org:80 (138.195.130.70), connection timed out

W: Failed to fetch http://nightlies.videolan.org/build/intrepid-i386/arch/./en_US.bz2  Unable to connect to nightlies.videolan.org http:

W: Failed to fetch http://ubuntusoftware.info/dists/intrepid/Release.gpg  The HTTP server sent an invalid reply header

W: Failed to fetch http://ubuntusoftware.info/dists/intrepid/all/binary-i386/Packages.gz  Bad header line

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

so do u have any solution for this??

---

### Post by lady_jade on 2009-01-30
I have been having a similiar problem. I installed ubuntu a fresh and decided to update open office, now I get this as open office won't update and I can't use any office files like word, excel etc:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

thats the error I get.

---

### Post by bbzzdd on 2009-01-30
Did you recently add Gnome-Do to your apt sources?  If so, you need to add their public key to your source list.

Grab the key here:

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x7D2C7A23BF810CD5](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x7D2C7A23BF810CD5)

And save it to a text file.  Go to System->Administration->Software Sources->Authentication and import that key file.

---

### Post by Santooka on 2009-01-30
so in the end, did u find any solution??

did u know how to update??

---

### Post by lvlo on 2009-01-31
In terminal run:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys $KEY
```
then
```
gpg --export --armor $KEY | sudo apt-key add -
```
where $KEY is key value you have missed. Do those 2 commands for each repository which you have problem.

---

### Post by leonardo_neo on 2009-01-31
> **lvlo said:**
> In terminal run:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys $KEY
```
then
```
gpg --export --armor $KEY | sudo apt-key add -
```
where $KEY is key value you have missed. Do those 2 commands for each repository which you have problem.

Dude, you rock! :D

I was having the same problem after manually upgrading Open Office 2.4 to 3.
After the upgrade I was getting the same message. So I did what you said, and voila, the problem is gone!

Thanks buddy. :D

---

### Post by Santooka on 2009-01-31
but i dunno what to replace $KEY with :S...

i am pretty new for this

---

### Post by thglara on 2009-01-31
:) I'm a brazilian Ubuntu user. I did have this problem and now no more. Thanks

---

### Post by lvlo on 2009-01-31
> **Santooka said:**
> but i dunno what to replace $KEY with :S...

i am pretty new for this

Errors you've posted contain **$KEY** you need:```
...NO_PUBKEY **CA1F91146F087E5A**
```

Cheers :)

---

### Post by Santooka on 2009-01-31
ok very nice,

after doing what u have said to do... i only get this:

```
W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2  Unable to connect to wine.budgetdedicated.com http:

W: Failed to fetch http://nightlies.videolan.org/build/intrepid-i386/arch/./Release.gpg  Could not connect to nightlies.videolan.org:80 (138.195.130.70), connection timed out

W: Failed to fetch http://nightlies.videolan.org/build/intrepid-i386/arch/./en_US.bz2  Unable to connect to nightlies.videolan.org http:

W: Failed to fetch http://ubuntusoftware.info/dists/intrepid/Release.gpg  The HTTP server sent an invalid reply header

W: Failed to fetch http://ubuntusoftware.info/dists/intrepid/all/i18n/Translation-en_US.bz2  Bad header line

W: Failed to fetch http://ubuntusoftware.info/dists/intrepid/all/binary-i386/Packages.gz  Bad header line

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

so u have any idea what to do about these?

---

### Post by lvlo on 2009-01-31
Servers may be down. Wait for a while and try again.

---

### Post by Sale on 2009-01-31
Hi,

I have this problem too but the solution posted here dosn't work:
 When I try

```
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
```

I get this error:
```

gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: can't open `/home/sale/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

```

But when I try ```
sudo gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
``` here is what happens:
```

gpg: WARNING: unsafe ownership on configuration file `/home/sale/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
```

What does this mean?

TIA

---

### Post by lvlo on 2009-01-31
Cause you use:```
gpg --keyserver keyserver.ubuntu.com **--recv** 60D11217247D1CFF
```but right command will be:```
gpg --keyserver keyserver.ubuntu.com **--recv-keys** 60D11217247D1CFF
```

---

### Post by arch1k on 2009-01-31
Thank you very much. I had the same problem after manually upgrading Open Office 2.4 to 3.
After the: gpg --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF
everything is as smooth again. Ubuntu community rocks!

---

### Post by maudy on 2009-01-31
Thaaaaaank you!!!!
One more happy brazilian

---

### Post by Sale on 2009-01-31
ouch!

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF
gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: can't open `/home/sale/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

```

also with sudo:

```
sudo gpg --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF
[sudo] password for sale: 
gpg: WARNING: unsafe ownership on configuration file `/home/sale/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

```

How come everybody is happy but me? ;)

---

### Post by thehero on 2009-01-31
> **Sale said:**
> ouch!

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF
gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: can't open `/home/sale/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

```

also with sudo:

```
sudo gpg --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF
[sudo] password for sale: 
gpg: WARNING: unsafe ownership on configuration file `/home/sale/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

```

How come everybody is happy but me? ;)

Go to the /home/sale/.gnupg folder and check the file permissions for the files inside. The owner for the pubring.gpg file should be the user you are using.

---

### Post by chaehaih on 2009-02-01
Hi LvLo, 

Sorry I have a general question. What is the key and why some repositories require it.I got to this thread by inputting the error message I got for trying to install the Gnome-Do repository for Ubuntu 8.10 from: [http://do.davebsd.com/wiki/index.php?title=Installing_Do](http://do.davebsd.com/wiki/index.php?title=Installing_Do)

repository: 
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main


But I get an error message. so my question is: Must the keys be installed first before attempting to add a repository? 

Installing Do's website says, these are optional: 

gpg --no-default-keyring --keyring /tmp/gnome-do.keyring --keyserver keyserver.ubuntu.com --recv A5D19FDCAA6ABB440CD3464628A8205077558DD0
gpg --no-default-keyring --keyring /tmp/gnome-do.keyring --export --armor  A5D19FDCAA6ABB440CD3464628A8205077558DD0 | sudo apt-key add -
rm /tmp/gnome-do.keyring

I don't know which to input in the terminal first and how to input them. 

thanks for any help.

---

### Post by lvlo on 2009-02-01
Hi there :)

I don't know much about this stuff, but [**GnuPG faq page**]("http://gnupg.org/documentation/faqs.en.html#q1.1") says:
> GnuPG stands for GNU Privacy Guard and is GNU's tool for secure communication and data storage. **It can be used to encrypt data and to create digital signatures.**In a nutshell it's a secure feature.

Without GPG key you can add repositories as well, but you can't get information from there - it's encrypted.

How to add repositories you can find here: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Other%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Other%20Repositories)


Then just run these 3 commands in terminal to add GPG key of Gnome-Do repository:
```
gpg --no-default-keyring --keyring /tmp/gnome-do.keyring --keyserver keyserver.ubuntu.com --recv A5D19FDCAA6ABB440CD3464628A8205077558DD0
``````
gpg --no-default-keyring --keyring /tmp/gnome-do.keyring --export --armor  A5D19FDCAA6ABB440CD3464628A8205077558DD0 | sudo apt-key add -
``````
rm /tmp/gnome-do.keyring
```


Update software information and install Gnome-Do by these commands:```
sudo apt-get update && sudo apt-get install gnome-do
```

---

### Post by chaehaih on 2009-02-01
thanks man :) Will give it a shot.. I am a total noob.. :( just learning to use it via ubuntu kung fu book..

---

### Post by Sale on 2009-02-01
> **thehero said:**
> Go to the /home/sale/.gnupg folder and check the file permissions for the files inside. The owner for the pubring.gpg file should be the user you are using.



Thanks thehero, this finally worked out! :)

I wonder how did the file get to have the wrong owner in the first place (root was the owner)???

---

### Post by juanbretti on 2009-02-01
> **lvlo said:**
> In terminal run:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys $KEY
```
then
```
gpg --export --armor $KEY | sudo apt-key add -
```
where $KEY is key value you have missed. Do those 2 commands for each repository which you have problem.
Thanks! That was the solution! To all my Ooo, GnomeDo and SMPlayer problems! Thanks!

Thanks!

---

### Post by lady_jade on 2009-02-01
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

The above link helped as I got the key. Thanks a lot guys I really love the fact that there is this community where we can help others and get help when we need it as well.:popcorn:

---

### Post by veeravalli on 2009-02-01
> **lvlo said:**
> In terminal run:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys $KEY
```
then
```
gpg --export --armor $KEY | sudo apt-key add -
```
where $KEY is key value you have missed. Do those 2 commands for each repository which you have problem.
Thanks! You solved my Open Office problem, too.

---

### Post by acreech on 2009-02-03
> **lvlo said:**
> In terminal run:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys $KEY
```
then
```
gpg --export --armor $KEY | sudo apt-key add -
```
where $KEY is key value you have missed. Do those 2 commands for each repository which you have problem.

Thanks for the info. That worked great for me. 

acreech

---

### Post by kiprit on 2009-02-04
> **lvlo said:**
> In terminal run:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys $KEY
```
then
```
gpg --export --armor $KEY | sudo apt-key add -
```
where $KEY is key value you have missed. Do those 2 commands for each repository which you have problem.

works perfect!
I tried a couple of time until i realized that i also needed to replace the $ sign in the code as well :D

---

### Post by optimistique1 on 2009-02-04
Hi please can someone help.
I have followed some of the instructions to resolve this same problem.
However, when I run update manager I keep getting:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF.

I get this when I try and also update open office in the 'software sources' along with ANYTHING that has the words ppa.launchpad.net it seem :-(

What can I do to resolve this?

---

### Post by lvlo on 2009-02-04
Well, try this:```
gpg --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF && gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
```

---

### Post by optimistique1 on 2009-02-10
> **thehero said:**
> Go to the /home/sale/.gnupg folder and check the file permissions for the files inside. The owner for the pubring.gpg file should be the user you are using.

Hi the owner is saying root and there is no option to change it...
How do I change the owner to myself?
Many thanks
Garry

---

### Post by rsay on 2009-02-10
Assuming the username is "sale"

```
sudo chown sale:sale /home/sale/.gnupg/*
```

This will set the owner/group to sale for all the files in the /home/sale/.gnupg folder.

---

### Post by optimistique1 on 2009-02-10
Hi Buddy I am now getting the following error - 

root@Garry:~# gpg --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF && gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
gpg: WARNING: unsafe ownership on configuration file `/home/garry/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
root@Garry:~#

---

### Post by ginnie6 on 2009-02-12
I was having the same problem...I tried Gnome do and have not updated since. I had already removed it though. I tried importing the key again...no luck. I saw that there was a gnome do key still there so I deleted it and am now updating.

---

### Post by lvlo on 2009-02-12
> **optimistique1 said:**
> Hi Buddy I am now getting the following error - 

root@Garry:~# gpg --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF && gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
gpg: WARNING: unsafe ownership on configuration file `/home/garry/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
root@Garry:~#Hi :)
Why are you running this command in ROOT terminal? Maybe that is a reason of messed permissions. Try to run it like normal user or (if you did it in ROOT terminal) like above:```
sudo chown $USER:$USER /home/$USER/.gnupg/*
```where $USER - your user name.

---

### Post by acsworrell on 2009-02-13
This worked for me as well, thank you very much!

---

### Post by forger on 2009-02-14
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by anjilslaire on 2009-02-27
> **lvlo said:**
> In terminal run:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys $KEY
```
then
```
gpg --export --armor $KEY | sudo apt-key add -
```
where $KEY is key value you have missed. Do those 2 commands for each repository which you have problem.

+1
Agreed. This works well.

---

### Post by sgosnell on 2009-02-27
What you're getting is just a warning.  You don't have to do anything about it.  Open Office will install fine without the key.  It's just a warning that the package manager can't verify the files.  As long as you know where they're coming from, just continue and don't worry about it.  Keys aren't really necessary.

---

### Post by jmthomas on 2009-03-15
Thank you very much for the help.

This was driving me nuts.

---

### Post by marionspd on 2009-04-27
Worked for me - Thanks!

---

### Post by tocker on 2009-05-12
> **lvlo said:**
> ...a couple of code lines...

Thanks lvlo! it worked.

<gripe>
I'm just wondering why every time I do something in Ubuntu, I have to go through the whole process of searching and digging for a solution (which 99% of the time is a couple of command lines).

I like Ubuntu and force:) my family to use it. But I would be cautious to recommend it to anyone who is either code-illiterate or doesn't have the time and energy to search for fixes.

In this particular instance, if I manually, deliberately, add a Software Source, why isn't the key loaded automatically :confused: (at least prompt me to do so). If I can do it anyway, why not make it straightforward?
</gripe>

---

### Post by sgosnell on 2009-05-12
I don't know how that would work.  If you manually add a repository, then you have to manually add the key, because the program has no way of knowing where the key is, or even if it exists.  There is no requirement to use a key, and there is no requirement to use it if there is one.  It's just a little extra security.  If you manually add a repository, you presumably know it's safe, and installing the key doesn't do a lot of good.  

If you have to do something in Windows or OSX, you have to do the same searches, unless you already know how to do it.  It's the same with anything else - if you don't know how to do something, you have to learn how to do it.  This is not at all unique to Ubuntu.

---

### Post by gksmithlcw on 2009-07-05
> **thehero said:**
> Go to the /home/sale/.gnupg folder and check the file permissions for the files inside. The owner for the pubring.gpg file should be the user you are using.

> **rsay said:**
> Assuming the username is "sale"

```
sudo chown sale:sale /home/sale/.gnupg/*
```

This will set the owner/group to sale for all the files in the /home/sale/.gnupg folder.


> **lvlo said:**
> In terminal run:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys $KEY
```
then
```
gpg --export --armor $KEY | sudo apt-key add -
```
where $KEY is key value you have missed. Do those 2 commands for each repository which you have problem.

Thanks to all of you! Ubuntu is great and it is so because of its community!

---

### Post by gksmithlcw on 2009-07-05
> **sgosnell said:**
> If you have to do something in Windows or OSX, you have to do the same searches, unless you already know how to do it.  It's the same with anything else - if you don't know how to do something, you have to learn how to do it.  This is not at all unique to Ubuntu.

You are quite right.... Us Windows folks who have been using Windows for so long take our acquired knowledge for granted. Thanks for putting up with us! LOL

---

### Post by MTHarden on 2010-01-13
> **lvlo said:**
> Cause you use:```
gpg --keyserver keyserver.ubuntu.com **--recv** 60D11217247D1CFF
```but right command will be:```
gpg --keyserver keyserver.ubuntu.com **--recv-keys** 60D11217247D1CFF
```

This worked for me too. Thanks!

---

### Post by compaz1 on 2010-01-13
> **pepemosca said:**
> Thanks! That was the solution! To all my Ooo, GnomeDo and SMPlayer problems! Thanks!

Thanks!

Thanks LVLO

You guys are way too much help.

---

### Post by theadictspunk on 2010-02-06
Worked Great! Remember to do both commands! thanks!

---

### Post by 2kquik on 2010-06-22
[COLOR=black]Thanks lvlo! This fixed my problem.
[/COLOR]

---

### Post by kishore.r.318 on 2010-06-29
all i get is that the keyserver timed out. tried out several times now. 
is there some other means to get the public key?

---

### Post by sam_w on 2012-05-18
Thanks a lot for the help, very useful :)

---

### Post by oldos2er on 2012-05-18
Old thread closed. Please don't bump old threads.

---

