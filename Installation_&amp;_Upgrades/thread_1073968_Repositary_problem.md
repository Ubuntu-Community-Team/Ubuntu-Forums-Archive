---
title: "Repositary problem?"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by frankwakeman on 2009-02-18
I'm getting this error message when I try to reload in Synaptic:

"W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  



W: Some index files failed to download, they have been ignored, or old ones used instead."

Is this related to other postings regarding Synaptic here?  Or how can I put this right?  My other computer has Linux Mint and is fine.  for example, for both computers I wanted to replace the startup jungle with the one from Ubuntu Studio; this worked for Linux Mint but not Ubuntu.  While distro-hopping I've installed Ubuntu 8.10 three times and never had this occur before.  Things like Emerald aren't available either.

Thanks in advance for any help.

---

### Post by taurus on 2009-02-18
Try changing to another server in synaptic.

---

### Post by frankwakeman on 2009-02-18
I've tried a few with no luck.  The erro warning doesn't come up, but I still can't get the programs I'm after which should be there: Emerald, Scribus and that Ubuntustudio-sounds.

sudo apt-get update didn't work either.

---

### Post by taurus on 2009-02-18
What is the complete output when you ran that command from a terminal?

```
sudo apt-get update
```

---

### Post by frankwakeman on 2009-02-19
Thanks for your help.  The output is:

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security Release                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/multiverse Sources
Reading package lists... Done


Before I changed to different repositary sources it additionally also contained the error message in my first post here.  If it's not doing that now I'm puzzled as to why if I type in Emerald or Scribus nothing comes up.  What do you think?

---

