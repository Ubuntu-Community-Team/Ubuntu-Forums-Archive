---
title: "Update Manager Not Working"
date: 2008-10-18
forum: General Help
---

### Post by 173jay on 2008-10-18
Whenever i try to use update manager i receive the following error message, i have searched for a solution but am struggling to understand some of the suggested actions.
I relatively new to Linux & would appreciate any help/advice.
Thanks
Jason

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead

---

### Post by plucky on 2008-10-18
Open a terminal window by **Applications > Accessories > Terminal** and copy and paste this command ```
sudo apt-get update
```
It will ask for your password,which is your login password,but will not echo any output.


Post any errors back to the forum.

If no errors,then try ```
sudo apt-get upgrade
``` to install any updates.


Good Luck

---

### Post by linuxbastard on 2008-10-20
Hi,

I'm getting the same issue.  The first sign of the issue started a few days ago.  I was getting this yellow (orange) triangle on my notification area that asks me to check for updates.  when I click the icon, it launches the update manager, where I get a notice that my last update was seven days ago.  When I click on "check" in update manager, I get this error:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

I tried the method you mentioned here and I still get the same error in terminal with:
```
# sudo apt-get update
```

I saw in some other posts that it may be a problem with some third party software sources, but as you can see, the issue is with an Ubuntu repository.

Any other ideas on what could be happening?

---

### Post by plucky on 2008-10-20
> I saw in some other posts that it may be a problem with some third party software sources, but as you can see, the issue is with an Ubuntu repository.

Any other ideas on what could be happening? 


Try another Server.Go to **System > Administration > Software Sources** and select another server and try to reload using the terminal command ```
sudo apt-get update
``` and post the output of any errors.


Good Luck

---

