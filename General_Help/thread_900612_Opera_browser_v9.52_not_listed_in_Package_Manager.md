---
title: "Opera browser v9.52 not listed in Package Manager"
date: 2008-08-25
forum: General Help
---

### Post by TimDaniels on 2008-08-25
The latest version of Opera web browser, version **9.52**, has been downloadable from the Opera website for more than a week, but the Package Manager in Ubuntu 8.04 still lists version 9.27 (3 versions back).  Clicking on the Package heading in the GUI table doesn't reveal any other version as an option.  How does one tell the Package Manager to list version 9.52 of Opera and to download and install it?

If I were to download and install Opera manually, would **Package Manager** be able to uninstall it?

If I were to download and install Opera manually, would **Add/Remove** be able to uninstall it?

*TimDaniels*

---

### Post by forger on 2008-08-25
The synaptic package manager yes, I don't know about add/remove but I suppose so that it could.

Why don't you try it out?

You download the .deb package from: [http://www.opera.com/download/](http://www.opera.com/download/)
install it by double-clicking.

Ubuntu amd64 (64-bit) users have to install it using:
```
sudo dpkg --force-architecture -i path/to/file.deb
```

By the way, what operating system are you using? Opera has been removed from the repositories, they're not allowed to redistribute it:
[http://packages.ubuntu.com/search?keywords=opera](http://packages.ubuntu.com/search?keywords=opera)

---

### Post by gladstone on 2008-08-25
Opera have their own repository that is safe to add:

[http://deb.opera.com/](http://deb.opera.com/)

I use
```

deb http://deb.opera.com/opera-beta/ lenny non-free

```
in "Software Sources"

Heres a thread if you need some help [deb.opera.com repository not updated to opera 9.50b2 ?](http://my.opera.com/community/forums/topic.dml?id=231514) (note, they are updating it again - my Opera updated to 9.52 with apt nicely :))

---

### Post by forger on 2008-08-25
newsflash: 9.5x is now stable :) [http://deb.opera.com/](http://deb.opera.com/)
use: deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free

for the key:
```
sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

---

### Post by TimDaniels on 2008-08-25
> **forger said:**
> The synaptic package manager yes, I don't know about add/remove but I suppose so that it could.

Why don't you try it out?

You download the .deb package from: [http://www.opera.com/download/](http://www.opera.com/download/)
install it by double-clicking.

Ubuntu amd64 (64-bit) users have to install it using:
```
sudo dpkg --force-architecture -i path/to/file.deb
```

By the way, what operating system are you using? Opera has been removed from the repositories, they're not allowed to redistribute it:
[http://packages.ubuntu.com/search?keywords=opera](http://packages.ubuntu.com/search?keywords=opera)

I'm using Ubuntu 8.04.  I see from the Ubuntu "packages" page that Opera is not listed, although the Ubuntu 8.04 that I downloaded 10 days ago has a Package Manager that lists Opera v9.27.  Perhaps v9.27 was the last one downloadable by Package Manager?

*TimDaniels*

---

### Post by jerome1232 on 2008-08-25
> **forger said:**
> The synaptic package manager yes, I don't know about add/remove but I suppose so that it could.

Why don't you try it out?

You download the .deb package from: [http://www.opera.com/download/](http://www.opera.com/download/)
install it by double-clicking.

Ubuntu amd64 (64-bit) users have to install it using:
```
sudo dpkg --force-architecture -i path/to/file.deb
```

By the way, what operating system are you using? Opera has been removed from the repositories, they're not allowed to redistribute it:
[http://packages.ubuntu.com/search?keywords=opera](http://packages.ubuntu.com/search?keywords=opera)

Actually if you are using 64 bit that site gives you a 64 bit .deb, the browser is actually 64 bit now. Now if only adobe would follow suite.

---

### Post by forger on 2008-08-25
> **jerome1232 said:**
> Actually if you are using 64 bit that site gives you a 64 bit .deb, the browser is actually 64 bit now. Now if only adobe would follow suite.
True, I just saw it in the package pool :)

> I'm using Ubuntu 8.04. I see from the Ubuntu "packages" page that Opera is not listed, although the Ubuntu 8.04 that I downloaded 10 days ago has a Package Manager that lists Opera v9.27. Perhaps v9.27 was the last one downloadable by Package Manager?

Maybe it was the last downloadable version :)
I suggest doing:
```
sudo apt-get autoremove --purge
sudo apt-get autoclean
sudo apt-get update
```

---

### Post by TimDaniels on 2008-08-25
> **gladstone said:**
> Opera have their own repository that is safe to add:

[http://deb.opera.com/](http://deb.opera.com/)

I use
```

deb http://deb.opera.com/opera-beta/ lenny non-free

```
in "Software Sources"

Heres a thread if you need some help [deb.opera.com repository not updated to opera 9.50b2 ?](http://my.opera.com/community/forums/topic.dml?id=231514) (note, they are updating it again - my Opera updated to 9.52 with apt nicely :))

In **Package Manager | Software Sources | Third-Party Software** I have checked: "http://archive.canonical.com/ubuntu hardy partner", but the Package Manager still lists Opera v9.27 in the "World Wide Web (partner)" category.

I can't figure out how you were able to get v9.52.

*TimDaniels*

---

### Post by cybrsaylr on 2008-08-25
I've always downloaded Opera from their site with no problems.

A couple days ago they released v9.52 and I upgraded to that with no problems off the Opera website.

---

### Post by forger on 2008-08-25
> **TimDaniels said:**
> In **Package Manager | Software Sources | Third-Party Software** I have checked: "http://archive.canonical.com/ubuntu hardy partner", but the Package Manager still lists Opera v9.27 in the "World Wide Web (partner)" category.

I can't figure out how you were able to get v9.52.

*TimDaniels*

can you post the output of this command in terminal:
```
apt-cache policy opera
```
Here's mine:
> 
$ apt-cache policy opera opera-static
opera:
  Installed: 9.52.2091.gcc4.qt3
  Candidate: 9.52.2091.gcc4.qt3
  Version table:
 *** 9.52.2091.gcc4.qt3 0
        500 [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages
        100 /var/lib/dpkg/status


Edit: the canonical partner repository is outdated, use: ```
deb http://deb.opera.com/opera/ lenny non-free
```
(it's **[COLOR="Red"]without the -beta[/COLOR]** part!)

---

### Post by TimDaniels on 2008-08-25
> **forger said:**
> can you post the output of this command in terminal:
```
apt-cache policy opera
```

I got:

opera:
  Installed: (none)
  Candidate: 9.27-20080331.6hardy1
  Version table:
     9.27-20080331.6hardy1 0
        500 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages

> 
Edit: the canonical partner repository is outdated, use: ```
deb http://deb.opera.com/opera/ lenny non-free
```
(it's **[COLOR="Red"]without the -beta[/COLOR]** part!)


I added the "deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free" line to my /etc/apt/sources.list file, and I ran:
 "sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -"
per the deb.opera.com web page, but the command returned an error:

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

and "reload" on Synaptic Package Manager reported the error:

W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791

There seems to be something missing.  Can you tell me what it is and how to get it?

*TimDaniels*

---

### Post by TimDaniels on 2008-08-25
> **TimDaniels said:**
> 
I added the "deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free" line to my /etc/apt/sources.list file, and I ran:
 "sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -"
per the deb.opera.com web page, but the command returned an error:

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

and "reload" on Synaptic Package Manager reported the error:

W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791

Now, in the category "World Wide Web (non free)", the Package Manager lists:

Opera            9.50-20080422.6     Opera browser
Opera-static     9.50-20080422.1     Opera browser

But still no version 9.52.

*TimDaniels*

---

### Post by forger on 2008-08-26
Can you reply with the output of these commands:
(Note: Copy and paste them **line by line** in terminal using right-click > paste)
```
uname -a
cat /etc/issue
wget --version | head -n 1
wget http://deb.opera.com/archive.key -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get autoclean
apt-cache policy opera

```

---

### Post by TimDaniels on 2008-08-26
> **forger said:**
> Can you reply with the output of these commands:
(Note: Copy and paste them **line by line** in terminal using right-click > paste)
```
uname -a
cat /etc/issue
wget --version | head -n 1
wget http://deb.opera.com/archive.key -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get autoclean
apt-cache policy opera

```

Thanks for your persistenct, Forger.  I finally broke down yesterday and downloaded the Linux Opera v9.52 manually, and let the GDEBI installer do the installation.  (I didn't do any un-taring or extraction, etc.)  That got v9.52 running so that I could try it out regarding Flash and mouse forward/backward buttons.  (Flash works, but the for/back mouse buttons still do not work, although they work for Firefox.)

In reading the comments in the Ubuntu-supplied /etc/apt/sources.list file, I decided to just flush the crap and have it contain just one line - **deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) lenny non-free** - the one you had given me.  Then I did a Reload in Synaptic Package Manager, and voilà!  The "World Wide Web (non-free)" category now has version 9.52 of Opera.

I think all the other deb command lines in sources.list were either confusing Package Manager or overriding your line, since I had originally put it near the beginning of the file.  Now the question is: Will that one line suffice for getting upgrades security updates?

*TimDaniels*

---

### Post by TimDaniels on 2008-08-26
> **forger said:**
> Can you reply with the output of these commands:
(Note: Copy and paste them **line by line** in terminal using right-click > paste)
```
uname -a
cat /etc/issue
wget --version | head -n 1
wget http://deb.opera.com/archive.key -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get autoclean
apt-cache policy opera

```


<slaps head> OK, I realized that /etc/apt/sources.list was for a lot more software than just Opera, so I put the "deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) lenny non-fre" line at the end of the sources.list file.  I then clicked on Package Manager's "Reload", and an error message eventually came up about Opera and no public key.  But the category "World Wide Web (partner)" still containd the entry for **Opera** as version 9.52.

Here are the results of running the commands you listed:

$ uname -a
Linux laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

$ cat /etc/issue
Ubuntu 8.04.1 \n \l

$ wget --version | head -n 1
GNU Wget 1.10.2

$ wget [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) -O- | sudo apt-key add -
```

--17:19:03--  [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key)
           => `-'
Resolving deb.opera.com... 195.189.143.183
Connecting to deb.opera.com|195.189.143.183|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,742 (1.7K) [application/pgp-keys]

100%[====================================>] 1,742         --.--K/s             

17:19:04 (78.76 MB/s) - `-' saved [1742/1742]

OK

```

$ sudo apt-get update
```

Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://archive.canonical.com hardy Release                                 
Hit http://us.archive.ubuntu.com hardy Release.gpg                   
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US       
Get:1 http://deb.opera.com lenny Release.gpg [189B]                            
Ign http://deb.opera.com lenny/non-free Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US    
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Packages    
Hit http://security.ubuntu.com hardy-security/main Sources           
Get:2 http://deb.opera.com lenny Release [1068B]                     
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/universe Packages      
Hit http://security.ubuntu.com hardy-security/universe Sources       
Hit http://us.archive.ubuntu.com hardy/main Packages                 
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Ign http://deb.opera.com lenny/non-free Packages
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://deb.opera.com lenny/non-free Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Fetched 190B in 1s (124B/s)
Reading package lists... Done

```


$ sudo apt-get autoclean
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del linux-image-2.6.24-19-generic 2.6.24-19.36 [18.4MB]
Del linux-headers-2.6.24-19 2.6.24-19.36 [8131kB]
Del linux-headers-2.6.24-19-generic 2.6.24-19.36 [644kB]
Del opera 9.50-20080422.6 [6166kB]

```


$ apt-cache policy opera
```

opera:
  Installed: 9.52.2091.gcc4.qt3
  Candidate: 9.52.2091.gcc4.qt3
  Version table:
 *** 9.52.2091.gcc4.qt3 0
        500 http://deb.opera.com lenny/non-free Packages
        100 /var/lib/dpkg/status
     9.27-20080331.6hardy1 0
        500 http://archive.canonical.com hardy/partner Packages

```


Now after clicking "Reload" in Package Manager, there is a category "World Wide Web (non free)" with an entry for **Opera-static** as version 9.52!  It appears that the commands that you had me run satisfied the public key requirement, and the Opera-static entry was added.  Is that "Opera-static" entry from the Lenny repository?


*TimDaniels*

---

### Post by forger on 2008-08-27
well mine is opera, i don't have opera-static
> $ apt-cache policy opera-static
opera-static:
  Installed: (none)
  Candidate: (none)
  Version table:

Good, now you have it in your repositories, and you'll probably be able to grab all the stable packages in the future :)

edit:
Can you post your /etc/apt/sources.list file one last time? Just to be sure

---

### Post by TimDaniels on 2008-08-27
> Can you post your /etc/apt/sources.list file one last time? Just to be sure

/etc/apt$ cat sources.list

```

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe

##Added for the Opera browser:
deb http://deb.opera.com/opera/ lenny non-free

```

As you can see, there's a lot of entries, with the Opera "Lenny" entry at the very end.  Will that suffice to get the security patches and other updates?

*TimDaniels*

---

