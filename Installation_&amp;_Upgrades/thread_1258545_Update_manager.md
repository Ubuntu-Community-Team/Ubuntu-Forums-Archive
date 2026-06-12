---
title: "Update manager"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by jamsh on 2009-09-05
Recently my Update Manager returns the following message:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


How do I rectify this??

---

### Post by tommcd on 2009-09-05
This is a problem with the Opera repo you have added to your sources.list. If you comment out (put a # in front of) the opera repo in your sources.list the error should be gone.
If you wish to continue using the Opera repo, you will have to add the GPG key for that repo. The instructions for how to add the GPG key are on the Opera repo page:
[http://deb.opera.com/](http://deb.opera.com/)
**Ubuntu users**
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -

```
This should (hopefully) fix the problem and allow you to use the Opera repo.

---

### Post by jamsh on 2009-09-05
Excellent,fixed.   Thanks Tommmcd

---

### Post by OwnName on 2009-09-07
Thanks tommcd, very helpful. Also, pretty weird for me they save their own sources.list file called opera.list in a dedicated folder named /etc/apt/sources.list.d/

---

### Post by bnvdarklord on 2009-09-07
Didn't work for me.... how can i do it manually?

---

### Post by bnvdarklord on 2009-09-07
anyone?

---

### Post by tommcd on 2009-09-08
> **bnvdarklord said:**
> Didn't work for me.... how can i do it manually?
The command I posted in my last post is the manual way.

What problem are you having? Are you getting the same error that Jamsh was getting, which was caused by a missing GPG key for the Opera repo? Or are you getting a different error?

Post the output of:
```
sudo apt-get update
```
And also post your: /etc/apt/sources.list

---

### Post by tommcd on 2009-09-08
> **OwnName said:**
>  Also, pretty weird for me they save their own sources.list file called opera.list in a dedicated folder named /etc/apt/sources.list.d/
The medibuntu repo (assuming you have added it) also lives in the /etc/apt/sources.list.d/ directory. The purpose of the sources.list.d directory (as I understand it anyway) is to keep 3rd party repos separate from the main Ubuntu repos for easier management of sources. I don't think it is strictly necessary to have a separate directory for these 3rd party repos though. See these links for some more info:
[http://ubuntuforums.org/archive/index.php/t-586222.html](http://ubuntuforums.org/archive/index.php/t-586222.html)
[http://manpages.ubuntu.com/manpages/jaunty/man5/sources.list.5.html](http://manpages.ubuntu.com/manpages/jaunty/man5/sources.list.5.html)

---

### Post by bnvdarklord on 2009-09-08
> **tommcd said:**
> The command I posted in my last post is the manual way.

What problem are you having? Are you getting the same error that Jamsh was getting, which was caused by a missing GPG key for the Opera repo? Or are you getting a different error?

i got it to work, i used this command first 
```
sudo apt-get install debian-archive-keyring
```
and then 
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```
thanks anyway.:)

---

### Post by subhas123 on 2009-09-08
Unable to connect to the internet.

I have installed Ubuntu 9.04 in my system. The installation is successfully completed. But I am unable to connect to the internet. Please let me know the procedure about how to connect to the internet.

Thanks 
Subhas.

---

### Post by OwnSurname on 2009-09-08
Dear subhas123,
this thread is about an update manager problem. Your problem seems different, so you should start another thread for it. Also, you should be more specific, writing down what are you doing, with what and how, and the error you read in the output, in case you're looking for help.

---

### Post by sowjendra on 2011-02-17
Thank you very much.. your solution has fixed up my problem

Regards
Surendra

---

