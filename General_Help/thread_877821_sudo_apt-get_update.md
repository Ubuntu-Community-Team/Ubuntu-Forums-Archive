---
title: "sudo apt-get update"
date: 2008-08-02
forum: General Help
---

### Post by chrispche on 2008-08-02
I'm getting this when I run this command:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

Any ideas as to whats going on here?

Thanks.

---

### Post by drs305 on 2008-08-02
It could be a problem with a specific server. Try opening synaptic > settings > repositories > download from > other > select best server.

Or System > Admin > Software Sources >> 'Download from' and pick another server.

---

### Post by zvacet on 2008-08-02
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by SunnyRabbiera on 2008-08-02
Could be a server or something, try the command and it might be good.
This is the issue with using third party repositories.

---

### Post by chrispche on 2008-08-02
Still getting this and I changed servers.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by jualin on 2008-08-02
How about adding the key to your machine by running > sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by drs305 on 2008-08-02
If jualin's method was sufficient, you may need to redo your medibuntu sources list.

The way to include the Medibuntu repository changed with the introduction of Hardy. If you used old commands to add it the medibuntu.list may not be correct. The following will install  the Medibuntu Repository following the guidance from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). 

```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-old 
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by chrispche on 2008-08-02
Ok I'm getting this:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
medibuntu-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  dpatch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And at the end of the update I get this message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

Is this serious, or a problem at medibuntu's end?

---

### Post by drs305 on 2008-08-02
> **chrispche said:**
> 
Is this serious, or a problem at medibuntu's end?

I just reran the 3 lines and it all worked fine. Would you please post your sources.list? 
```

cat /etc/apt/sources.lst

```

---

### Post by plucky on 2008-08-02
Try this line to add the key.I have found the previous line fails if it thinks the key is already installed.


```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Good Luck

---

### Post by zvacet on 2008-08-02
In terminal type

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -

---

### Post by chrispche on 2008-08-05
> **plucky said:**
> Try this line to add the key.I have found the previous line fails if it thinks the key is already installed.


```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Good Luck

Thank you very much that's done the job. Just out of interest, could you explain what was going on here. I'm an intermediate Linux use so you don't have to be too basic. Just a general explanation would be nice.

---

### Post by plucky on 2008-08-05
> **chrispche said:**
> Thank you very much that's done the job. Just out of interest, could you explain what was going on here. I'm an intermediate Linux use so you don't have to be too basic. Just a general explanation would be nice.

As I understand it is wget fetch the file medibuntu-key.gpg from [http://packages.medibuntu.org/](http://packages.medibuntu.org/) as a file and pipes it to apt-key to update your list of trusted keys.

For further reading ```
man wget
man apt-key
```

Good Luck

---

### Post by jualin on 2008-08-06
Glad to hear that you got the problem sort out. Nice way to tackle the problem Plucky. :)

---

