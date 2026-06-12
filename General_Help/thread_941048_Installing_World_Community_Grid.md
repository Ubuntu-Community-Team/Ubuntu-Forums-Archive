---
title: "Installing World Community Grid"
date: 2008-10-07
forum: General Help
---

### Post by r1ch on 2008-10-07
Hi everyone... 
I am trying to install the World Community Grid client for linux and straightforward information is difficult to come by.

Is anyone able to point me towards a beginners level tutorial (generic or otherwise) on how to do this please?

All I have so far is a file downloaded from the WCG website with the filename...

boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh

and I can find no mention of any world community grid package in the add/remove programs dialog or synaptic.

The 'installing on linux' page of the WCG website is also shamefully thin on installation details!

For reference if it is relevant I'm on 8.10 beta.

Thanks

---

### Post by phidia on 2008-10-07
Open a terminal from Applications > Accessories and enter "./" before the shell script you have. That would look like this: > ./boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh 
Note: You need to be in the directory that contains that script.
And you may need to used "sudo" in front of "./"

---

### Post by r1ch on 2008-10-07
Thankyou for you help, unfortunately it does not seem to work, and says 'command <filename here> does not exist'

---

### Post by r1ch on 2008-10-07
Aha! Just found out to right click, select properties and tick the allow execute box. Double clicking and running in the terminal extracted a folder with what looks to be significantly more useful files.

---

### Post by ju2wheels on 2008-10-08
> **r1ch said:**
> Aha! Just found out to right click, select properties and tick the allow execute box. Double clicking and running in the terminal extracted a folder with what looks to be significantly more useful files.

You should really not be using that installer. That is an old version of Boinc. Boinc is actually already in the Ubuntu repositories, so you can do the following:

```

sudo apt-get install boinc-client boinc-manager

```

You can then access the Boinc Manager from Applications->System Tools->Boin Manager.

The latest bleeding edge version can be downloaded from the Debian repositories.

---

