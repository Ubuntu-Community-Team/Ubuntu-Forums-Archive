---
title: "I need help from Synaptic Package Management!"
date: 2008-09-10
forum: General Help
---

### Post by kyme on 2008-09-10
Guys I'm new in Ubuntustudio & not that much good debugging some error.
 I have tried open my Synaptic Package Management.
 a message occurred and appear that :


> 
 W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9.  

 And sometimes it do appears on this 
 > 
  YOU HAVE 2 BROKEN PACKAGES ON YOUR SYSTEM! 
  USE THE BROKEN FILTER TO LOCATE THEM.
 

    How do i solve this issue and where i can find the broken filter so i can locate them?
    

    I'm using UBUNTUSTUDIO right now NOT SURE IF IT IS OR JUST UBUNTU 7.10,
    I got trouble installing ubuntustudio before so when i got the theme
    its already appear and look like ubuntustudio. So not sure if my
    pc is already running a ubunstudio. Anyway, Is it the same configuraion
    with ubuntu 7.10
   
  :confused: Please help me and i really need it badly for my pc.
    please do email me for respond <redacted> or 
   chat me in Yahoo msnger or send me private message. I will just always 
   update this thread. Your help appreciated much..Thanks.!

---

### Post by zxscooby on 2008-09-10
from: [https://help.ubuntu.com/community/SecureApt?highlight=%28synaptic%29%7C%28no%5C_pubkey%29](https://help.ubuntu.com/community/SecureApt?highlight=%28synaptic%29%7C%28no%5C_pubkey%29)


Validation of Release file and packages
Secure apt now verifies the Release file, which is updated each time any of the packages in the archive change. The Release file itself contains, among other things, md5 checksums of other files in the archive. If it cannot download the Release.gpg, or if the signature is bad, it will complain, and will make note that the Packages files that the Release file points to, and all the packages listed therein, are from an untrusted source. 
Here's what that looks like: 
```
W: GPG error: http://ftp.us.debian.org testing Release: The following signatures
 couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
```
If you ignore that warning and try to install a package later, apt will warn again: 
```
WARNING: The following packages cannot be authenticated!
  libglib-perl libgtk2-perl
Install these packages without verification [y/N]?
```
 Note that you can disable these checks by running apt with --allow-unauthenticated

---

### Post by 3rdalbum on 2008-09-10
It's safe to ignore for now because it won't affect your ability to install software or do anything else. But it's a warning that if packages downloaded from tuxfamily.org have been intercepted and modified in transit, then the package management system won't be able to detect this happening.

What you need is a GPG key file from tuxfamily.org. When you have obtained one, go to System > Administration > Software Sources and click the Authentication tab, then click "Import Key File". Select the GPG key file and reload the package list. The warning should no longer appear and your package manager will be as secure as you can expect.

---

### Post by kyme on 2008-09-10
> **3rdalbum said:**
> It's safe to ignore for now because it won't affect your ability to install software or do anything else. But it's a warning that if packages downloaded from tuxfamily.org have been intercepted and modified in transit, then the package management system won't be able to detect this happening.

What you need is a GPG key file from tuxfamily.org. When you have obtained one, go to System > Administration > Software Sources and click the Authentication tab, then click "Import Key File". Select the GPG key file and reload the package list. The warning should no longer appear and your package manager will be as secure as you can expect.

 Sir, i already did go to the System->Administration->Software Source and
 then click the Authentication tab & click "import key file". but then
 i couldnt select the GPG key file cause it was not there it was pointing 
 to the folder where there is desktop folder and Documents, Public, templates, 
 Video, Public, etc.. 
 What is GPG key? it did not appear to the directory file?
 Is there any other way..?

---

### Post by silverglade00 on 2008-09-10
It is somehting you download from tuxfamily.org

---

### Post by oldos2er on 2008-09-10
To fix broken packages, run "sudo aptitude install -f" in a terminal.

---

### Post by kyme on 2008-09-10
> **oldos2er said:**
> To fix broken packages, run "sudo aptitude install -f" in a terminal.

 That is what i type in Terminal..
 And it appear on this.
 > 
 W: GPG error: [http://ftp.us.debian.org](http://ftp.us.debian.org) testing Release: The following signatures
 couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
 
  same it did appear... How will i stop the appearing the msg box 
  every time i open the synaptic package manager?
  Help me :-( im so poor debugging...

---

### Post by kyme on 2008-09-11
pls help, still wont work!! :-(

---

### Post by kyme on 2008-09-11
still need help

---

### Post by oldos2er on 2008-09-11
> **kyme said:**
> That is what i type in Terminal..
 And it appear on this.
 
  same it did appear... How will i stop the appearing the msg box 
  every time i open the synaptic package manager?
  Help me :-( im so poor debugging...

 Go download the public key for debian.org.

---

