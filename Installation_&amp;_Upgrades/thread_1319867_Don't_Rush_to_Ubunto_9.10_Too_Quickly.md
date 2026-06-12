---
title: "Don't Rush to Ubunto 9.10 Too Quickly"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-11-08
On my PC, Ubuntu 9.10 did not work out as an upgrade from version 9.04.  I guess it could be even worse if you have an earlier version of Ubuntu.  And I am not thrilled with what I see in Ubuntu 9.10 after a clean install.  In some ways, it is more like Windows, particularly Vista, than Microsoft imposed on us.  You might want to put off the upgrade for a bit until some issues are addressed and fixed.  Question that comes to light is, who is the real boss here?  You, or some criteria set forth by someone more concerned about corporate security?
You try it, you should probably see what I mean in short order.

Trouble with a clean install is, what happens to the work you have on your existing install?  An upgrade should take care of that, if it worked like it is suppose to.  But maybe you had better think about doing a backup first, or find some other way to protect that work.

Here is what I decided to do:  I wanted to copy just my work to another drive.  But where is my work?  Under my user account in the /home folder, of course.  So can I just copy /home or /username to another drive?  That should work, though the applications that you need for that work will not go with this.  But the applications should be downloadable and reinstallable, and the work then recovered by copying back what you saved to the same /home structure that you copied it all out of.

I tried to use the GUI to peform the copy process, because you can do a copy and paste between views of what you want to save from and where you want to copy to.  Trouble is, root cannot run from the GUI (one of those decisions made in favor of security), so to do it you have to enter the terminal mode and use the sudo su or the sudo -s command to become super user.

Now you have to find whatever internal partition or external drive you want to copy to.  For most, these will show up under Places/Computer or Places/Removable Media.  Once you verify what it is named, you use the Terminal mode to create a folder on that partition or drive named home or home1, of something like that.  then to perform the copy from the present Ubuntu install to the new folder, you would enter a command something like this:

    cp -r /home/* /media/drivename/foldername

Of course you replace drivename with the name that appears for that drive in /media, and foldername with whatever you named the new folder to be.  It can take awhile for the copy to complete, but that should do it.

Now you do the new Ubuntu 9.10 install either over the existing version or somewhere else on a free partition.  When this boots up,
go back to the place where you copied to, and go up in the folder tree until you find the user-named folder.  Don't go into that folder,
but again, use that name in the following comman:

    cp -r /media/drivename/folders up to useraccount/* /home

If you do this right, then this will show you the user account in /home:

    dir /home
           username

if instead you see this:
           home
or something like this:
           Desktop

Then you copied from a level too low or from a level too high and got it wrong.  That means cleaning up by using the rm -r * command and trying it again with some slight difference in fhe cp parameters.

Ubuntu 9.10 is suppose to have or get the latest and greatest of everything, so don't plan on ignoring it forever.  But on my PCs, I still maintain installs of 9.04 and 8.04 as well.  In some ways, they just feel better to me.

---

### Post by Klunk on 2009-11-08
I dont understand what you are getting at here. Firstly you complain that Ubuntu is too much like windoze and then you complain that you cant do a GUI copy and have to drop into a command line.

You could always tar up your home directory onto your backup drive and then untar it into your new install. Oh and BTW, isnt it a good idea to check what you have copied BEFORE you do the install rather than wait until you do the install to find you have copied at the wrong level?

---

### Post by issih on 2009-11-08
For future reference if you need to copy and paste things involving root owned folders you just need to hit alt+f2 or open a terminal and run:

```
gksudo nautilus
```

That will open the file manager with root privileges - obviously you should therefore be very careful with it....

So all those steps are entirely unnecessary.

As for the mini rant...I'll just ignore that if that's allright with you.

---

### Post by QIII on 2009-11-08
The rant is human.  We all do it from time to time.

Your answer is aimed at averting the rant in the future by virtue of instruction.

+1.  ```
gksudo nautilus
```

But I would add going to the terminal and getting all of your .debs for your installed applications in order so that you can dpkg the .debs back to have your installed applications back quickly when you are done with the FRESH INSTALL with a separate /home partition.

Use nautilus to copy your separate /home directory to a network drive or another drive on the same machine.

Clean install without touching the /home directory.  Have the original saved in case there are some unexpected results.

dpkg your .debs.  (Sorry, you may have to go to some trouble with third-party apps.)

Easy.  No mess.  No fuss.  Clean install without upgrade horror.

---

### Post by issih on 2009-11-08
Not 100% sure if you meant this by what you said, but as a general rule I would not recommend copying debs over from one release to another. Sure it often works...but its still not a great idea.

If you want to get all the same apps installed quickly then follow this advice:

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

To get a list of your installed apps and punt that back into apt-get in the new release.

This will mean that your apps will all be pulled from the repositories of the new release, rather than installing versions of applications pulled from the previous release's repos (with all the potential compatibility nightmares that could induce)

Now, I'm sure that dpkg is smart enough to note that the deb you are installing is available in the repos and offer you the choice of how you want to deal with that...so you probably can end up with things correctly set up even if you do do this, but you could also get it very wrong. All in all its just a bit of a funny way to go about it to my mind.

---

### Post by theozzlives on 2009-11-08
All your stuff in /home if you had a seperate /home partition:
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")
the install process is the same from one version to another, and you can't upgrade from anything earlier than 9.04.

P.S. you can't even spell Ubuntu!

---

### Post by QIII on 2009-11-08
Much better, issih!

---

### Post by mrojas73 on 2009-11-09
My Dell XPS M1530 upgreaded just fine no issues at all.

---

