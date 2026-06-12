---
title: "Syncronize or share bookmarks on dual-boot?"
date: 2008-09-13
forum: General Help
---

### Post by 2CV67 on 2008-09-13
Hi guys!

I am dual booting Hardy with XP (FAT32).

I have Firefox 3.0 in both.

When I recently did a clean install of Hardy, I transfered my bookmarks etc from XP OK, but since then they have naturally drifted apart.

I wondered what methods there were to synchronize them.

I found a couple of on-line methods, like Foxmarks > [http://www.foxmarks.com/](http://www.foxmarks.com/)
but that looks like a sledgehammer to crack a nut & I see suggestions it slows things down & I am not too sure about uploading all that stuff to the web...

Then I found this article which suggests sharing the same profile between both versions of Firefox. Neat!
> [http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/](http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/)

Well, I followed that, pointing my new Ubuntu FF profile at my existing XP FF profile & with a couple of reservations, it certainly works, for bookmarks & also (whether you want it or not...) for all the other aspects of Firefox.

Snags I encountered were:
1. Initially, FF would not start in Ubuntu, with an error message about the profile being already in use.
This was because the XP partition was not mounted, so I had to remember to click on my XP drive before opening FF in Ubuntu.
I suppose there are several ways round that, but I copied the XP profile to my Shared partition & redirected both Ubuntu & XP Firefoxes to that one.
Works OK but now I need to set up a backup procedure for that remote profile.

2. Every time I switch between Ubuntu & XP, when I open Firefox, I get a warning that "6 new add-ons have been installed" (in XP) and "3 new add-ons have been installed" (in Ubuntu).
This carries on, not just one time.
There is no way of seeing what the 6 & 3 new items are (is there?) but listing the various items under "add-ons" shows differences mainly between the plugins in Ubuntu & XP.
Is there some way to escape from these warnings or do I just have to live with it?

Is there any better way of synchronizing or sharing bookmarks on dual-boot set-ups?

Thanks!

---

### Post by lovinglinux on 2008-09-13
I don't think sharing profiles is a good idea, because some extensions are not compatible with Linux and a corrupted profile can give you a lot of trouble.

If you just want bookmark sync, Foxmarks is the way to go. I works pretty fine both ways. Just make sure you set it up to auto update on exit.

If you want to share other settings like cookies, passwords and other stuff and you don't switch between OS's very often, you could install FEBE and CLEO extension on both and backup/restore your profile (excluding extensions) every time you switch OS. If something goes wrong with your profile, you will at least have  working backups.

---

### Post by Ms_Angel_D on 2008-09-13
> **lovinglinux said:**
> If you just want bookmark sync, Foxmarks is the way to go.

+1

Foxmarks works perfectly for me :D

---

### Post by derjames on 2008-09-13
Hello there!

Firefox stores your bookmark information in a file called places.sqlite. This file is stored in your profile folder. In windows it can be found here:

```

C:\Documents and Settings\USER\Application Data\Mozilla\Firefox\Profiles\xxxxxxxx.default/places.sqlite
```

while in linux it can be found here:

```
/home/USER/.mozilla/firefox/xxxxxxxx.default/places.sqlite
```

The point is to copy this file from one of this locations to the other when an update occurs. For example you can create an script that checks for this and make the necessary changes. The script is shown below and it is followed by a brief description. Just remember to change USER with the appropriate ubuntu/windows user names and change the xxxxxxxx.default folder name to the ones on your profile (the names are not necessarily the same between operating systems). The script is written in python, I do apologize if there is a more elegant or simplified form to do this...


```

#! /usr/bin/python

# This script updates the bookmarks in a dual boot WindowsXP/Ubuntu machine
# The primary operation is to copy back and forth the file places.sqlite which contains
# the information of the firefox bookmarks
# Date 13-September-2008


import os
import stat
import time

def main():

	try:	
		os.system('clear')

		# windows side

		bookmarks_file_windows_side=os.stat('/media/disk/Documents and Settings/USER/Application Data/Mozilla/Firefox/Profiles/xxxxxxxx.default/places.sqlite')
		last_modified_win=time.ctime(bookmarks_file_windows_side[stat.ST_MTIME])
		print "= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = ="	
		print "Firefox bookmarks file on Windows was modified on %s " % last_modified_win

		# ubuntu side

		bookmarks_file_ubuntu_side=os.stat('/home/USER/.mozilla/firefox/xxxxxxxx.default/places.sqlite')
		last_modified_ubuntu=time.ctime(bookmarks_file_ubuntu_side[stat.ST_MTIME])
		print "Firefox bookmarks file on Ubuntu was modified on %s " % last_modified_ubuntu
		print "= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = ="

		# bookmark synchronisation
	
		if last_modified_ubuntu>last_modified_win:
			print 'Updating Firefox for Windows Bookmarks ...'
			command_file_to_copy="cp /home/USER/.mozilla/firefox/xxxxxxxx.default/places.sqlite '/media/disk/Documents and Settings/USER/Application Data/Mozilla/Firefox/Profiles/xxxxxxxx.default/places.sqlite'"
			os.system(command_file_to_copy)
			print 'Done.'
		else:
			print 'Updating Ubuntu Bookmarks ...'
			command_file_to_copy="cp '/media/disk/Documents and Settings/USER/Application Data/Mozilla/Firefox/Profiles/xxxxxxxx.default/places.sqlite' /home/USER/.mozilla/firefox/xxxxxxxx.default/places.sqlite"
			os.system(command_file_to_copy) 
			print 'Done.'
	
	except OSError:
		print "Windows drive is not mounted... please mount Windows drive and re-run the script..."
		
if __name__ == '__main__':
	main()

```

The script simply gets the last modification date of the two files immediately after the newer file replaces the older one. This preliminary version does not mount the Windows drive, if this is the case the script will indicate that and ask you to mount the drive afterwards you can execute the script.

I you choose to use this script save it somewhere in your hard drive, for example

```
/home/james/scripts
```

and give it a name, for example: updateBookmarks

then introduce this route to you path so it can be easily accessible by adding the following lines at the end of your .bashrc script

```
PATH=$PATH:/home/james/scripts
export PATH
```

source the .bashrc script (so you don't have to restart the system)

```
source ~/.bashrc
```

make the python script executable

```
chmod 755 updateBookmarks
```

run the script by typing 

```
updateBookmarks
```

If you are running Ubuntu, execute the script just after leaving your firefox session by simply running the above command. This will update the FIrefox for windows bookmarks

If you are running Firefox on Windows finish your session as usual.  Switch to linux, once on linux run the script before launching firefox. This will update your Bookmarks on Firefox for linux.

Just remember to mount the Windows partition first. Hope this helps.

j

---

### Post by 2CV67 on 2008-09-14
Thanks for all those helpful replies & special thanks to derjames for that long & detailed method!
Did you do all that just to answer my question?

I am still mulling over which way to go, as I hesitate to try anything as big/new/different/potentially-risky as what derjames suggested (not excluded though, I am still glad to have that as an option).
I guess I will stop sharing the profile anyway...

On Foxmarks: does it handle deletions OK, or does it keep 'synchronizing' to the fullest version, thus cancelling any deletion made in one version only?
I didn't see an answer to this in any of the pages I visited.

---

### Post by lovinglinux on 2008-09-14
> **2CV67 said:**
> On Foxmarks: does it handle deletions OK, or does it keep 'synchronizing' to the fullest version, thus cancelling any deletion made in one version only?
I didn't see an answer to this in any of the pages I visited.

It has full sync. As I said, you have to make sure you configure it to sync on exit, so every time you close Firefox on one OS it will sync with Foxmarks. This way you don't forget to sync after any changes. Additionally, you have options for manual upload and manual download. It will ask if you want to override your current bookmarks when doing it manually.

You could create fake profiles on both OS's and sync them back and forward, delete and add bookmarks, just to see how it works.

---

### Post by 2CV67 on 2008-09-14
Thanks!

I guess I will go that way.

For the moment, I am pausing this activity while I try to fix Firefox - broken probably as a result of sharing the profiles!

I went back to the default profiles in Ubuntu & in XP.
Ubuntu works just fine.
XP has developed a glitch where FF opens (via Profile Manager) fine first time after a boot, and maybe a few times afterwards, but eventually fails to open the Profile Manager, either from the Firefox launcher, or from a link in a mail or even running the command in the "run" box...
Same with the shared profile now & with a new copy of the backup copy I made before starting all this.

So may need to turn my attention to XP forums for a while!

---

### Post by 2CV67 on 2008-09-15
OK - it was not my fault!

By playing around, I discovered that the problem (can't open Firefox in XP) always started after I tried to open FF by clicking on a link in an e-mail.
After that it was impossible to open it at all (icon, link or "run" box) without a reboot.

Knowing that, I found it was a known bug in Firefox 3.0
> [http://kb.mozillazine.org/Browser_will_not_start_up#Firefox_3_will_not_open_if_started_from_an_Internet_shortcut_or_another_application](http://kb.mozillazine.org/Browser_will_not_start_up#Firefox_3_will_not_open_if_started_from_an_Internet_shortcut_or_another_application)

The workaround is:
> open the Profile Manager, select a profile, place a check mark in the "Don't ask at Startup" option and then start Firefox with that profile, to set it as the default. 

So now I can start looking at synchronizing again...

---

### Post by lovinglinux on 2008-09-15
I forgot to mention an alternative . Instead of using built-in Firefox Bookmarks, you could use [[COLOR="DarkRed"]**Scrapbook**[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/427") extension. It is an extension that allows you to save entire pages and organize them as menu trees. Nevertheless, it also allows to create bookmarks.

I use Scrapbook mainly for saving pages, but also to share bookmarks between Firefox profiles. If you setup the extension to "Enable Multi-Scrapbook" you can create and manage several scrapbooks in the same Firefox profile, saving them wherever you want. So you can save the scrapbooks in the Windows drive and load them into your Ubuntu Firefox profile. You don't even have to sync, because everything is saved in the scrapbook directory you choose. So, you can add, remove, rename bookmarks (or pages) and they will be available to any Firefox profile you have. You just need to add the directory using the Scrapbook options.

This is particularly useful when you don't want to share all bookmarks between profiles. For example, I have a profile that I use Brief extension for feeds and another profile that I have Feed Sidebar. Each feed reader has it's own advantages for different situations. The thing is that I don't want to load all feeds on both profiles, so I do not use Foxmarks, otherwise their feeds will be in sync. So I use Scrapbook to share only those bookmarks that I need on both profiles.

---

### Post by 2CV67 on 2008-09-15
Well - I have used Scrapbook for years but never noticed the bookmark facility (rtfm...).

I keep Scrapbook for saving pages "as is" before they get updated & lose content I want to keep.
Not the same job as bookmarking where you just want to save the address.
I will check on the bookmarking with Scrapbook & I am sure others will find that information useful - thanks!

Meanwhile, back at the desk, I copied my profiles & installed Foxmarks in both halves of my dual boot & was pleased it managed to "merge" the bookmarks without apparent loss or mess.
I tried some deliberate additions & deletions both ways, with mixed results, and am now running with it enabled.

It always notices any change I make & asks me whether to synchronize on shutting down FF, but it is very erratic in updating when I switch to the other OS.
Seemingly most times, it does not automatically synchronize (even though I have that option & all the others checked in the General settings box).
Closing an unaltered Firefox does not trigger an update either, but manually selecting "Synch now" brings in the latest version from the server OK.
Seems about the same either way between Ubuntu & XP.

I don't see any reports of this in my Googling so far.

Hmm...

---

### Post by 2CV67 on 2008-09-18
Ah! After several exchanges with the very helpful people at Foxmarks (thanks guys!) things are now clearer.

I had been expecting Foxmarks to automatically sync down from the server every time I opened Firefox in a different OS.

In fact (& it's difficult to find a description) Foxmarks may only sync after 60 minutes if you just closed FF in one OS & opened in another, without making any changes in the new OS (as I was doing in my tests).
Explained in this (obsolete?) wiki page:> [http://wiki.foxmarks.com/w/index.php?title=Foxmarks:_Product_Features&oldid=6201#How_does_automatic_synchronization_work.3F](http://wiki.foxmarks.com/w/index.php?title=Foxmarks:_Product_Features&oldid=6201#How_does_automatic_synchronization_work.3F)

If it has been more than 60 minutes since the latest sync, then Foxmarks will downsync automatically within about a minute of opening a new FF session, which I guess is usually OK.

Must be difficult to find settings which please all users, but maybe we can hope for some user-settable parameters for auto sync in some future version?

Thanks again for the helpful contributions in this thread & from Foxmarks support staff.

---

### Post by FidelDahan on 2008-09-20
I liked the script-based synchronization that derjames posted, because I don't want to upload my private bookmarks online (don't trust them).

So there is a simpler solution: just replace your Linux files with symbolic links pointing to the Windows files, and everything synchronizes automatically. Symbolic links are special files, that have no content, but only point to the real files instead. When a Linux-app like Firefox reads a symbolic link, it automatically reads the real file.

Basically you do need to replace these files in your Linux profile:

places.sqlite (bookmarks and history)
bookmarkbackups (backup folder for bookmarks)

0. Start Ubuntu, don't open Firefox

1. Open the Windows profile folder and select the files, then "Make Links". You get 2 files "Link to ...". Cut these symbolic links [CTRL+X].

2. Open the Linux profile folder and delete the files from the list above. Then paste the symbolic links [CTRL+V]. Now rename them [F2] to the original names (remove the "Link to ").

Now bookmarks should be always the same when you reboot in the other OS and you don't need to run scripts.

PS: sorry for the long explanation, I suppose anyone running a dual-boot would know how to make a symbolic link :)

---

### Post by 2CV67 on 2008-09-20
> **FidelDahan said:**
> PS: sorry for the long explanation, I suppose anyone running a dual-boot would know how to make a symbolic link :)

No! No! No! One of the problems with self-learning Ubuntu is that you can have enormous & surprising blind spots!

Thank you very much for the detail.

Thank you even more for the idea, which looks like exactly what I have been looking for - reliable, simple, bookmark sharing for dual-boot, without the risk & waste of uploading-downloading all that stuff.

I haven't tried it yet, but I suppose I should shift the Windows Profile (complete) to the Shared partition, to avoid needing to mount Windows partition (see post#1) unless there is an easier way?

After trying that, I shall start to wonder if there is a similar way of sharing passwords - I am even less enthusiastic about uploading/downloading them than bookmarks...

Thanks again FidelDahan :)

---

### Post by 2CV67 on 2008-09-20
Oh! :(

I tried the symbolic link method, but am unable to make links to the Windows file or folder.

I get an error message "Operation not permitted".
Same thing when acting as root.

I can make them OK to the Ubuntu file & folder.

A bit of Googling suggests symbolic links cannot be made in FAT32...

I did not dig very deeply into it so far.

Any suggestions please, while I am digging?

---

### Post by lovinglinux on 2008-09-20
> **FidelDahan said:**
> PS: sorry for the long explanation, I suppose anyone running a dual-boot would know how to make a symbolic link :)

Thank you. I didn't know about this feature, which is very useful for many situations. Every day I discover something new and really nice about Linux :popcorn:

---

### Post by 2CV67 on 2008-09-21
> **FidelDahan said:**
> I liked the script-based synchronization that derjames posted, because I don't want to upload my private bookmarks online (don't trust them).

So there is a simpler solution: just replace your Linux files with symbolic links pointing to the Windows files, and everything synchronizes automatically. Symbolic links are special files, that have no content, but only point to the real files instead. When a Linux-app like Firefox reads a symbolic link, it automatically reads the real file.

Basically you do need to replace these files in your Linux profile:

places.sqlite (bookmarks and history)
bookmarkbackups (backup folder for bookmarks)

0. Start Ubuntu, don't open Firefox

1. Open the Windows profile folder and select the files, then "Make Links". You get 2 files "Link to ...". Cut these symbolic links [CTRL+X].

2. Open the Linux profile folder and delete the files from the list above. Then paste the symbolic links [CTRL+V]. Now rename them [F2] to the original names (remove the "Link to ").

Now bookmarks should be always the same when you reboot in the other OS and you don't need to run scripts.

PS: sorry for the long explanation, I suppose anyone running a dual-boot would know how to make a symbolic link :)

That sounded exactly right, but unfortunately my XP (& shared partition) are FAT32.

As far as I can see, Ubuntu cannot make symbolic links pointing to files or folders in FAT32. (please correct all mistakes here & below...).

But:
I can put my XP Firefox profile in the FAT32 shared partition & FF works OK.
I can put my Ubuntu FF profile in the shared partition & FF works OK.
Windows can make links (short-cuts) to files & folders in the shared partition.

So: Should it be possible to rework FidelDahan's idea by:
Put both profiles in the shared partition.
Keep the Ubuntu profile as Master for bookmarks.
Replace the XP places.sqlite file by a short-cut to Ubuntu places.sqlite file renamed "places.sqlite"
Replace the XP bookmarkbackups folder by a short-cut to Ubuntu bookmarkbackups folder renamed "bookmarkbackups"

Or will that screw something up badly?
Or just not work?

Thanks for any comments!

---

### Post by 2CV67 on 2008-09-23
I posted about this on the Mozilla forum & got the following reply from 'the-edmeister' (thanks!)
> There is no "simple" solution. The developers made it impossible to share bookmarks in Firefox 3 as was possible with all previous versions.
[https://bugzilla.mozilla.org/show_bug.cgi?id=385077](https://bugzilla.mozilla.org/show_bug.cgi?id=385077) = WONTFIX

Reading through the linked thread is very interesting & seems to point to a big(?) new problem with Firefox 3 for many people.

---

### Post by fchristophersen on 2008-09-23
i tried fidel dahan's solution on a ntfs disk and it worked... thanks a lot!!!

---

