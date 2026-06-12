---
title: "Major Problems With Root-Account!!!"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by riwa on 2006-01-27
I can't use my root-account for anything (almost). Some few commands work in the terminal but most of the time nothing at all happens. I try to go to the system-admin-add-user, it prompts for password and then nothing. I did the sudo adduser thing. And it worked! Added a new account, logged in with the new account.. Tried the to open add-user thingy from panel again and it tells me it's the wrong password. I don't get it. I do NOT type the wrong password trust me but it doesn't work. I formatted and re-installed THREE times without success. No errormessage during installation...

What should i do? 

Other things that don't work is:

sudo apt-get update/install*  ->just prompts me for password but NOTHING 					happens. No error message no nothing. 

and pretty much everything that prompts for root-password except:

su -	--> that works FINE! 

I'm very confused...

Regards
Richard

---

### Post by jrib on 2006-01-27
Root is disabled in ubuntu for a reason, read about it here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo).  I have read that enabling the root account will break the gui admin tools.

Are you using your user password for sudo?  That's what you need for sudo, not the root password.  If you are, post the output of the 'groups' command (for your user).  And also the contents of /etc/sudoers.

---

### Post by riwa on 2006-01-29
First of all, since I'm the only user on this, and my password is complex,  my root and user passwords are the same. Secondly I realized that the problem don't show if I : 
su -      # and then
apt-get install    # or whatever

only if I try to use *sudo* from the user account. Unluckily I can't log in as root until I can configure the login-screen and i can't conmfigure the login-screen until i can log in as root. Here's what's in the /etc/sudoers.

### OUTPUT of: /etc/sudoers###

root 105558:~ # cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
root 105607:~ #

From the *groups* command I get the OUTPUT: *root*.

---

### Post by aysiu on 2006-01-29
There's no root account unless you do an expert installation.
If you're not an expert, don't do one. Do the regular installation.
If you are an expert, don't ask for help.

Please read the third link of my signature--it explains everything. You **never** need to enable a root account to log into in Ubuntu. You can, but it's complex... and it usually is more work than using the built-in sudo way of doing things.

Read the third link of my signature. Please.

---

### Post by riwa on 2006-01-29
I get this now when i try to update from root ~#
Have tried to switch the etc/apt/sources.list thing but without improvement. 
And YES I did do an expert installation. Is that the problem?

Fetched 4B in 1s (2B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release)  Unable to find expected entry  eb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/eb-src Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_eb-src_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/http://sec/ubuntu Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_http:__sec_ubuntu_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/breezy-security Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_breezy-security_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by aysiu on 2006-01-29
[QUOTE=riwa]
And YES I did do an expert installation. Is that the problem?[/QUOTE] It is if you don't know what you're doing. That's why it's called an expert install.

See, this is me doing an apt-get update from a regular (not expert) installation: ```
sudo apt-get update
password:
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Hit http://archive.ubuntu.com breezy Release
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 4B in 1s (3B/s)
Reading package lists... Done
``` Part of what makes the expert install *expert* is the fact that a root account and Ubuntu don't *natively* mix. You have to do some virtual somersaulting to get root working the way it does on other distros. Ubuntu, like Mac OS X, is **designed to work with sudo**, not a separate root account. When you use a separate root account, you're on your own... and probably an expert.

---

### Post by riwa on 2006-01-29
Ok. But I did the expert installation only because my normal failed like 3 time. Had an initrd or something that didn't work. So I decided to try it out. It worked. However my apt-get command didn't work quite well on my previous (with error message) installation of ubuntu. It just didn't find the package or told me the package was broken. So then what should I do? Can't I manage with the expert installation then? Should i re-install?

---

### Post by riwa on 2006-01-31
I guess people are more fond of picking than helping....

---

