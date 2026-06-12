---
title: "Disable password for mounting drives in Karmic"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by praveenthivari on 2009-11-01
Everytime I mount the drive it asks for password authentication. I could somehow disable it in Jaunty but in Karmic I do not find any options to that.

---

### Post by tudor117 on 2009-11-01
Try installing pysdm
Select the drives you want and tell it any user can mount.
Before you could go to "Administration" -> "Authorizations" and there were mounting rules. Somehow they're gone. However, pysdm does a great job.

---

### Post by praveenthivari on 2009-11-02
> **tudor117 said:**
> Try installing pysdm
Select the drives you want and tell it any user can mount.
Before you could go to "Administration" -> "Authorizations" and there were mounting rules. Somehow they're gone. However, pysdm does a great job.

Thanks I 'll install and try it out.

---

### Post by JBAlaska on 2009-11-02
You can add the drives to fstab, an easy way to do this is with ntfs-config:
```
sudo apt-get install ntfs-config
```

After installing make sure the drives you want to automount are currently UNMOUNTED, then start ntfs configuration tool from System, Administration and check the boxes next to the drives you want to mount. That will update fstab for you.

It's alot less complicated than pysdm, but not as powerful either..

---

### Post by NickJones on 2009-11-02
If I remember correctly there should be a drop down menu when you enter your password, with options like, "Remember My Authentication" tick that and it should be problem solved.
Nick

---

### Post by praveenthivari on 2009-11-02
> **NickJones said:**
> If I remember correctly there should be a drop down menu when you enter your password, with options like, "Remember My Authentication" tick that and it should be problem solved.
Nick

There is no option in Karmic, it was there in Jaunty

---

### Post by praveenthivari on 2009-11-07
> **JBAlaska said:**
> You can add the drives to fstab, an easy way to do this is with ntfs-config:
```
sudo apt-get install ntfs-config
```After installing make sure the drives you want to automount are currently UNMOUNTED, then start ntfs configuration tool from System, Administration and check the boxes next to the drives you want to mount. That will update fstab for you.

It's alot less complicated than pysdm, but not as powerful either..

Is there no way to just mount the drive when needed without asking for password instead of keeping them mounted always?:p

---

### Post by Bombenbach on 2009-11-07
I've just found this solution
[http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic](http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic)
an it works like a charm on my Karmic-Thinkpad! Hope it helps.

---

### Post by HoTMetaL on 2009-11-08
> **Bombenbach said:**
> I've just found this solution
[http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic](http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic)
an it works like a charm on my Karmic-Thinkpad! Hope it helps.

Thank you, thank you, **THANK YOU** for that link.

---

### Post by HoTMetaL on 2009-11-08
On further testing, that actually *did not* work for me. Ubuntu 9.10 _still_ kept asking for password, even after logging out and rebooting. **The solution:** edit the /etc/sudoers file directly (_not_ recommended for beginners!). It did work nicely though, after doing some reading first and learning the *proper* way to edit this permissions file.

---

### Post by praveenthivari on 2009-11-09
Thanks for the replies

But the problem now is, I installed the 'pysdm drive manager' and after that for any mounting or unmounting I have to go to use pysdm to do that. i.e those option wont work normally.
Uninstaling that soft doesn't solve the problem. So, now I cannot test the link posted by [Bombenbach]("http://ubuntuforums.org/member.php?u=840726")

---

### Post by Flecto on 2009-11-09
I tried editing the /etc/sudoers file so that I won't have to enter my sodu password everytime I want to use mount or umount. But it had no effect, no matter what I tried to put into the /etc/sudoers file, it always asked for my sudo password (only once of course)...
 
So what is the "proper" way to edit the sudoers file to get rid of the password prompt? How did you do it HoTMetaL?
 
Thanks for the help.

---

### Post by HoTMetaL on 2009-11-09
> **Flecto said:**
> So what is the "proper" way to edit the sudoers file to get rid of the password prompt? How did you do it HoTMetaL?
Hey Flecto. I should clarify why I edited the sudoers file first before explaining how to do it. I wanted to mount *encrypted TrueCrypt containers* (virtual drives) without Ubuntu asking for my password during every mount and unmount. For this, sudoers did the trick. The instructions, however, *will be different* for mounting _actual_ drives, so adjust accordingly:

[COLOR="DarkRed"]*** Warning: You should backup **/etc/sudoers** first! ***
*** Warning: Editing this file incorrectly can create serious security implications. ***
*** Proceed _ONLY_ if you know what you're doing. ***[/COLOR]

```

randomuser@ubuntu:~$ sudo visudo

```
Then, I added a line at the very END of the sudoers file:
```

randomuser ALL=NOPASSWD: /usr/bin/truecrypt

```
**Ctrl+O** to SAVE (save as /etc/sudoers - remove the ".tmp")
**Press Y** to confirm
**Ctrl+X** to EXIT
You'll need to log out and back into Ubuntu.

---

### Post by lee-anna-loo on 2009-11-10
I also minded typing my password every time, so I found this 

> Open terminal and enter:
sudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

Find the action id:
org.freedesktop.devicekit.disks.filesystem-mount-system-internal

Within that action id look for the line:
<allow_active>auth_admin_keep</allow_active>
and replace it with:
<allow_active>yes</allow_active>

Save the file and witness the drives mounted without entering an authentication password.

Thanks to this guy:
[http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic]("http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic")

---

### Post by praveenthivari on 2009-11-11
Anyway I am happy now with the drives mounted at the beginning itself with pysdm. As of now now happy with that and would try other options sometime in future.:D:D:D:D

---

### Post by joejoseph00 on 2009-11-11
> **praveenthivari said:**
> There is no option in Karmic, it was there in Jaunty

When I first was prompted for the password in Karmic, nothing worked because I thought it was asking for my admin password for accessing NTFS which I don't have because I never specified a password in NTFS, instead once I realized that I could enter my SU password then I got in.

I see others have suggestions for automatic mounting, perhaps this should be an option in the dialog box.  So optionally from the dialog box the lazy user should be able to click a checkbox for always try to mount this partition.  As well it should be remarked to enter the Ubuntu password otherwise people get confused as I did.

?

---

### Post by ankhi on 2009-11-24
> **lee-anna-loo said:**
> I also minded typing my password every time, so I found this 



Thanks to this guy:
[http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic](http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic)



This worked for me too!!! Thanks to Anna (as I couldnt open the link in office) and to the guy to helped her!!:KS

---

