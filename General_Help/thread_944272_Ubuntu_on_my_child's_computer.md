---
title: "Ubuntu on my child's computer"
date: 2008-10-11
forum: General Help
---

### Post by waly on 2008-10-11
Hello,

I have installed Ubuntu 8.04 on my child's laptop (I'm a Debian user but not very experienced). During the installation, when it asked for the user's name, I gave it the name of my child and a password. 

Now, I don't want him to perform any administrative tasks but I want him to be able to run all programs installed in the computer, including printing, scanning, burning cd's, etc..  So what should I do now? Should I create a new user for me with a new password so that I would be the administrator or should I create a new user and password for him? And how do I manage the the space in the /home partition?

Thank you for your help.

W.

---

### Post by thestig_992 on 2008-10-11
you can set a root password (your own password) and make you child's account an 'administrator'. they shouldnt be able to do anything system related without a root password. I would tend to just make yourself an new account though, and use that as an admin.

For setting up programs, printing, etc, you should be able to install/set up as an admin, and then the user will have suficient privlages to use that program. Printing i think needs to be set up as root, but anyone can then use those printers.

I dont know how to limit the space of the /home folder, but there is likely an administrative tool for that...
Also, i dont think that /home is a separate partition in ubuntu...although i may be wrong

---

### Post by iponeverything on 2008-10-11
goto :

System ->  Administration -> Authorizations

---

### Post by wdaniels on 2008-10-11
> **waly said:**
> when it asked for the user's name, I gave it the name of my child and a password.

> **thestig_992 said:**
> you can set a root password (your own password) and make you child's account an 'administrator'. they shouldnt be able to do anything system related without a root password.

This isn't quite right.

The default account created during an install will have full "sudo" (i.e. root) privileges and the password required will be your child's password not root's password. Giving root a password will just enable the root account for login.

So you need to create a new account for yourself and then remove admin group from your child's account (or remove admin from your child's and just enable root login, but that is not recommended for security - root is not enabled by default for a reason).

As for quotas on the home directory, you can install the quota package, but I have no experience using it and I don't know of any GUI:

```
sudo apt-get install quota
```

---

### Post by steveneddy on 2008-10-11
IMO - I would just set up a new account for the child and you administer the machine, remotely if necessary.

It would be easier this way and if you remotely administered the machine from another PC in your house across your home network, they would never know that you were ever there. You could perform all updates to the system while they were using the machine and never know the difference.

Since you would be the only one with a root password, you could watch their online activity remotely also.

Remote administration and child online security takes on many faces, especially when it is your child.

Don't be afraid to look in on your child (remotely if necessary) while they are online.

They are going into an adult's world and you occasionally need to hold their hand in that world.

---

### Post by bodhi.zazen on 2008-10-11
> **thestig_992 said:**
> you can set a root password (your own password) and make you child's account an 'administrator'. they shouldnt be able to do anything system related without a root password.

I am sorry, but that advice is just bad advice.

First, there is no need to enable the root account.

Second, enabling the root account will not prevent the OP son from obtaining root access via sudo.

The proper solution is, as has been suggested, using your son's account create a new user. Make the new user an administrator (a member of the admin group), then log out and in as the new user. With the new user account remove your son's account from the admin group.

---

### Post by weatherkid on 2008-10-11
For kids I would suggest Edubuntu because that has ALOT of educational tools. Its a very simple upgrade. I think if you Google Edubuntu Add-On CD it should be the first hit. Just burn the .iso and stick it in when Ubuntu is fully up and running.:KS

---

### Post by waly on 2008-10-12
Hello, sorry to be back to you so late but it seems that only Sunday is giving me a chance to keep up with my work. Thank you very much to all of you for your answers, I've thought about all the possibilities you suggested and decided to follow the procedure of adding a new account, give it administration rights, then cancel my son from the administration group.
This seems to be working just fine, the only thing is that when entering my son's account, I can still install and disinstall application. How could I avoid this?

I'm also wondering why Ubuntu does not enable the root account by default, I quite not see what's the difference between using sudo and entering as root. What is the use of the root account as opposed to sudo?

One last thing, my son likes all the eyecandy of msn messenger, and I'm having trouble making him understand that Pidgin is better since it accepts all protocols and thus will enable him to communicate with more people. Is it possible to add skins, icons and  emoticons to Pidgin? Will he be able to save the emoticons he receives in Pidgin while he is involved in a conversation? He does this with MSN messenger and he loves it.

steveneddy,  you wrote:

"It would be easier this way and if you remotely administered the machine from another PC in your house across your home network[...]"

I woull love to be able to do that, but my knowledge  on that topic is equal to zero. I am willing to learn though, could you recommend any readings?


weatherkid, thank you for your suggestion, I think I will install Edubuntu once I've finish setting up the system.

---

### Post by Sef on 2008-10-12
> One last thing, my son likes all the eyecandy of msn messenger, and I'm having trouble making him understand that Pidgin is better since it accepts all protocols and thus will enable him to communicate with more people. Is it possible to add skins, icons and emoticons to Pidgin? Will he be able to save the emoticons he receives in Pidgin while he is involved in a conversation? He does this with MSN messenger and he loves it.
Much better than pidgin for that is either amsn or emesene.  Both are available in Add/Remove.  (Applications > Add/Remove > SHOW: all available applications > SEARCH: type in amsn or emesene > Apply Changes > Apply > Close

I have used both and emesene is what I prefer.   I use amsn if I am using a webcam, as emesene does not have that capability.    They, with Pymsn, into [one application]("http://www.linuxinet.com/linux-news/amsn2-join-amsn-and-emesene-pymsn.html") instead of the separate ones.

---

### Post by bodhi.zazen on 2008-10-12
For your question re: root see this:

[uwiki]RootSudo[/uwiki]

The bottom line is that yes su and sudo both give root access, sudo has a number of advantages including security and allowing partial root access (sudo can be configured to allow access to some but not all applications).

As far as your son's account accessing installation of applications, that is unusual. You need to log out (rather then switch user) and back in for permissions to take effect.

---

### Post by waly on 2008-10-12
> **bodhi.zazen said:**
> For your question re: root see this:
You need to log out (rather then switch user) and back in for permissions to take effect.

Thank you, this solved the issue.

Sef, thanks for your suggestion. I've installed aMSN and added some nice skins and icons, so I think he will be happy.

Thank you all for your help!

---

### Post by somersetsimon on 2008-10-13
> **waly said:**
> Thank you, this solved the issue.

Sef, thanks for your suggestion. I've installed aMSN and added some nice skins and icons, so I think he will be happy.

Thank you all for your help!

Hi - I have a related question. We have a spare desktop that the kids use (7 year old boy and 4 year old girl). It's currently running XP, but they don't use any specific windows applications - mainly web-based apps.
The XP setup lets me a startup page with an icon+name for each user. I have a password on my account, but not on their accounts. Can I set up the Ubuntu login page to do the same? I quite like the XP setup of having an icon next to your name - can I do this?
Thanks
Simon

PS I do have an ulterior motive for this. I'm planning on using the same machine as a MythTV backend and this would save the hassle of explaining to my wife why I need another computer in the house!

---

### Post by wdaniels on 2008-10-15
> **somersetsimon said:**
> I quite like the XP setup of having an icon next to your name - can I do this?

Yes, but you cannot set the pictures from the standard user manager. If you log into each account and go to Preferences->About Me you can set the picture there.

Also you need to use a login window that has a "face browser". I think by default Ubuntu has one called "Human List" (unless it's new for Intrepid) or you can find one more to your taste at [http://gnome-look.org](http://gnome-look.org) (select "GDM Themes" from the categories on the left).

You can change and install new login windows via the Administration->Login Window option.

---

### Post by somersetsimon on 2008-10-16
> **wdaniels said:**
> Yes, but you cannot set the pictures from the standard user manager. If you log into each account and go to Preferences->About Me you can set the picture there.

Also you need to use a login window that has a "face browser". I think by default Ubuntu has one called "Human List" (unless it's new for Intrepid) or you can find one more to your taste at [http://gnome-look.org](http://gnome-look.org) (select "GDM Themes" from the categories on the left).

You can change and install new login windows via the Administration->Login Window option.

Hi,
Since posting, I read about the planned new developments to the 'login experience' for 8.10. (See here [https://wiki.ubuntu.com/DesktopTeam/Specs/GdmFaceBrowser](https://wiki.ubuntu.com/DesktopTeam/Specs/GdmFaceBrowser)). It looks like that should do everything I want, so I think I'll wait for that.
Simon

---

### Post by thestig_992 on 2008-10-16
> **bodhi.zazen said:**
> I am sorry, but that advice is just bad advice.
What i said:
*First, there is no need to enable the root account.*

Second, enabling the root account will not prevent the OP son from obtaining root access via sudo.

The proper solution is, as has been suggested, using your son's account create a new user. Make the new user an administrator (a member of the admin group), then log out and in as the new user. With the new user account remove your son's account from the admin group.

Thats not exactly what i meant; 
[IMG]http://img360.imageshack.us/my.php?image=screenshotes1.png[/IMG]
enableing this will allow users to run things as root. I did not mean enable the root account, and i appologise if thats what it sounded like.

---

### Post by bodhi.zazen on 2008-10-16
> **thestig_992 said:**
> Thats not exactly what i meant; 
[IMG]http://img360.imageshack.us/my.php?image=screenshotes1.png[/IMG]
enableing this will allow users to run things as root. I did not mean enable the root account, and i appologise if thats what it sounded like.

Thank you very much for the clarification. It is sometimes difficult to know these things from reading what is posted (ie it is sometimes difficult to "read between the lines" if you will).

---

### Post by gjoellee on 2008-10-16
Go to System->Administration->Users and Groups. Now unlock the account and then select the account again and click on properties. 
Now go to the "User Privileges" and select the options you want your child to have. Click OK and that should be it...

In the worst case all you have to do is to make him a new account if it doesn't work.

Regards Gjoellee

---

