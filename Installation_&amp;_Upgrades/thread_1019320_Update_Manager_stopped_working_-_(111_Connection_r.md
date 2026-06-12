---
title: "Update Manager stopped working - (111 Connection refused)"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by someoneelse on 2008-12-23
Hi!  I've been using Ubuntu for about six months now, starting with 8.04 and updated to 8.10 (about a month or so ago, using the Update Manager).  However, eight days ago I stopped getting updates. 

In the Update Manager, just below where it says "Your system is up-to-date", it now also says "The package information was last updated eight days ago." When I click on the "Check" button, I get the following errors:

> 
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.


I did a search of the forums and found a few others who have had the same problem.  

Following the advice in _[Update Maneger Problem]("http://ubuntuforums.org/showthread.php?t=983179&highlight=update+manager+111+Connection+refused")_, I edited my "/etc/apt/sources.list" to reflect intrepid instead of hardy (I made a backup of my original sources.list file and then replaced the contents of the live one with a copy of ibizatunes file).  This did not fix the problem.

Following the advice in _[cannot update the system...please help]("http://ubuntuforums.org/showthread.php?t=996850&highlight=update+manager+111+Connection+refused")_ (nearly identical error messages), I have verified that I do indeed have internet access (I'm typing this from the afflicted machine) and that my /etc/hosts file is correct. Also, I get identical error messages from Synaptic (when I click the "Reload" button) and when I run "sudo apt-get update" from the command line.  I uninstalled anon-proxy (the offending proxy in minchiachina's case).  Update Manager still didn't work.  

I thought back, and realized that just before things stopped working, I ran the following: ```
sudo apt-get install mixmaster privoxy polipo socat tor-geoipdb
```  So I used synaptic to uninstall all of those programs.  I'm *still* getting the same error messages!

**[COLOR="Red"]Argh!!!![/COLOR]**  I'm pulling out what little hair I have left! ](*,) Does anyone have any other suggestions for what might be causing this sudden inability to update?

Thanks in advance for any assistance that you can provide in resolving this!

(Quick background info on me:  I've been using linux off and on for 13 years now.  Just previous to trying Ubuntu, I was using Fedora Core for about two years.  I know my way around the command line.  All the more reason why I'm frustrated at not being able to resolve what is most likely a simple mis-configuration somewhere! ;) )

---

### Post by kostkon on 2008-12-23
Could you please check that Direct Connection is set in *System &#8594; Preferences &#8594; Network Proxy*.

---

### Post by someoneelse on 2008-12-23
Direct connection is selected.

However, Update Manager *sort of* started working this morning... it said that there are 987 updates available.  However, when I go to actually do the update, I still get the same error messages.  Grrr....

---

### Post by tech9 on 2008-12-31
are you using ntlmaps?

---

