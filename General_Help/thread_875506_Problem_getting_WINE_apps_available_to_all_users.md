---
title: "Problem getting WINE apps available to all users"
date: 2008-07-30
forum: General Help
---

### Post by Luke3026 on 2008-07-30
I followed the instructions posted in this thread
[http://ubuntuforums.org/showthread.php?t=527169](http://ubuntuforums.org/showthread.php?t=527169)

I have 2 users -- me (administrator) & my son (restricted user).  I installed several WINE apps, then followed the instructions in the other thread.  I copied home\luke\.wine to home\wine and created the link in both my account and my son's.  Created a group, "plugdev", and added both accounts to it and set up the permissions on \home\wine as instructed.

But when logged in as my son, I cannot run any WINE app.  It tells me "\home\hunter\.wine is not owned by you".  The folder comes up as owned by my user account.

I'm still very much a Ubunty newbie, so maybe it's just that I'm not clear on ownership and permissions. What do I need to do to get this working?

Thanks!

---

### Post by DagMan on 2008-07-31
Have you checked to see that he is in the plugdev group?
anyhow, since it is a restricted account, and I'm making an assumption here which is that since you used plugdev instead of cdrom that you didn't want him using the cdrom... doesn't matter really and if it doesn't apply then no worries, but to point out that you can make a user group specifically for these purposes by doing 
```
sudo groupadd wineshared
```
to create a group called wineshared
then you would add a user to it like this
```
sudo gpasswd -a wineshared
```
then you'de use the chown command with the group name
```
chown youruser:wineshared somefolder -R
```
for example, or without the -R for a file.
Your group permission would for most purposes want to be the same as the owner permissions.

Sorry if that was horribly redundant to what you already learned 5 years ago or something.

I don't see anything wrong with the tutorial. If it isn't a group permission then try in addition.
```
chmod 775 /home/wine -R
``` but it's sort of done already, just in another manner, I think, in the tutorial.

To check you son's groups to make sure he is in the one assigned to wine
```
sudo groups hunter
```

I can't see what might be happening, failing oversights like that

---

### Post by Luke3026 on 2008-07-31
Thanks, I'll check what you suggested today.  May even start over and use the cdrom group.  I justed used plugdev since it was the example in the tutorial.

I'm sure this all is just some stupid mistake I made somewhere down the line. I'm still only 2 months into my Linux adventure here. :)

---

### Post by Luke3026 on 2008-07-31
I tried all of the above with no luck.  I still get a "\home\hunter\.wine is not owned by you" error when trying to run any WINE app as hunter (resticted user)

I created a new group, wineshared, added luke (my account) and hunter to it, changed the group of the shared WINE folder "\home\wine" to wineshared with permissions to create and delete files. Set up the linked folders in "\home\[username]\.wine" to point to "\home\wine".

Confirmed that hunter is a member of wineshared.

I can run all WINE apps logged in as luke.

This beginning to get frustrating.:confused:

---

### Post by DagMan on 2008-07-31
That is indeed baffling.
Just to emphasize in case you missed it, that missing this would cause it.
```
sudo chmod 775 /home/wine -R
```
You might also try, just for good measure
```
sudo chmod 775 /home/wine
sudo chmod 775 /home/hunter/.wine -R
sudo chown :wineshared /home/hunter/.wine -R
sudo chown :wineshared /home/wine -R
```

But to be quite honest, that seems redundant and it really sounds like you've followed things properly already, unless you missed the 'chmod' commands.
Maybe, and I'm pulling at straws, if you remove the symlink from your son's account,
```
sudo rm /home/hunter/.wine
```
and then log in as him and create the link again using his account. So from a terminal at his home directory.
```
ln -s /home/wine .wine
```

If it won't run like that, the last thing I can think of before surrendering to being stumped, is telling wine where the wine folder is, instead of using the link to the folder, so he would start an application by, at the command line, instead of doing something like this
```
wine "/home/hunter/.wine/path/to/some/application.exe"
```
try like this
```
WINEPREFIX="/home/wine" wine "/home/hunter/.wine/path/to/some/application.exe"
```
and if that works, athough I think it won't, then you can actually get rid of that WINPREFIX part by exporting it as his own variable on login but that's getting way ahead of where we are.  I'll keep the page bookmarked in case it does work in that manner but I'm not very optimistic, and quite frankly I don't know why it didn't work so I'm really sorry I couldn't be of more help.  Hopefully more people look at the thread despite it having multiple replies already.  I'm stumped.

---

### Post by Luke3026 on 2008-07-31
I tried all of the above with no success.  At this point I'm just going to totally uninstall Wine, pretend none of this ever happened, and start from scratch using that tutorial.

Thanks for your help so far.  I'll report back with an update.

---

### Post by Luke3026 on 2008-07-31
For the love of God!!

Totally uninstalled WINE, deleted all associated files and folders.  Reinstalled WINE and one app.  Followed the tutorial to the letter, and end up with the same error ".wine is not owned by you" when running a Wine app as hunter.  I can run them fine as luke (me).

I guess all I can do now is install the apps on both accounts, but I'm hesitant to do this since these apps take up a tone of space and this machine doesn't have the biggest drive.

Any other ideas??

---

