---
title: "[SOLVED] Firefox bookmark toolbar folder arrows"
date: 2008-09-06
forum: General Help
---

### Post by 2CV67 on 2008-09-06
Since Hardy (I think) all the folders in my Firefox bookmarks toolbar have developed a "drop-down" arrow.
The result is that all my folders no longer fit in one toolbar.
This is negative progress!

Googling, I found an Ubuntu Brainstorm item which offers a solution I am incapable of understanding, though it looks short & sweet!

[http://brainstorm.ubuntu.com/idea/7722/](http://brainstorm.ubuntu.com/idea/7722/)

This also points to a Hardy Development thread on the subject: 
[http://ubuntuforums.org/showthread.php?t=732134](http://ubuntuforums.org/showthread.php?t=732134)

Is this solution feasible for a "basic" user & if so, how exactly can I implement it?

Thanks in advance! :)

---

### Post by ryanhaigh on 2008-09-07
Ok I can see how that might be intimidating if you are not used to messing with firefox configurations.

First find your way to the chrome directory in your firefox profile, it should be somewhere like > /home/yourname/.mozilla/firefox/Profiles/XXXXXXX.default/chrome

Then open the file userChrome.css in your favorite text editor and add the line from the brainstorm page to the bottom of the file:
> #PersonalToolbar .toolbarbutton-menu-dropmarker display: none !important;

---

### Post by ryanhaigh on 2008-09-07
wow! tripple post

---

### Post by ryanhaigh on 2008-09-07
double post

---

### Post by Shazaam on 2008-09-07
"wow! tripple post" 
Yeah probably problems with the forums servers/databases. Forums were unreachable for 10 minutes.

---

### Post by 2CV67 on 2008-09-07
Thanks, ryanhaigh for what looks like a simple instruction.

When I try to do it though (I was going to say "as usual with Ubuntu" but I won't...) it turns out not to be so simple.

> First find your way to the chrome directory in your firefox profile, it should be somewhere like
Quote:
/home/yourname/.mozilla/firefox/Profiles/XXXXXXX.default/chrome 

There are no mozilla or firefox folders in /home/me/...
In the end I searched File System for "firefox" & found 7 folders:
"firefox" in /usr/lib
"firefox" in /usr/share
"firefox" in /usr/share/doc
"firefox-3.0" in /etc
"firefox-3.0" in /usr/share/bug
"firefox-3.0" in /usr/share/doc
"firefox-3.0.1" in /usr/lib

> Then open the file userChrome.css in your favorite text editor

Of the above folders:
"/etc/firefox-3.0/profile/chrome" contains a file "userChrome-example.css"
"/usr/lib/firefox-3.0.1/defaults/profile/chrome" also contains a file "userChrome-example.css"

Searching File System for "userChrome.css" finds nothing...

As you so rightly said:> Ok I can see how that might be intimidating if you are not used to messing with firefox configurations.


Yep!

---

### Post by 2CV67 on 2008-09-07
I found the instructions inside userChrome example & am going to try inserting the new line & saving it in firefox-3.0.1 as userChrome.css

Hope that is right!

---

### Post by 2CV67 on 2008-09-07
Well - I copied userChrome-examples.css as userChrome.css in /usr/lib/firefox-3.0.1/defaults/chrome & added the magic line, as root, keeping priorities.

Restarted Firefox - no change.

Rebooted PC - no change.

Would greatly appreciate further help!

See screenshot of modified userChrome.css

---

### Post by ryanhaigh on 2008-09-07
Ok 2CV67, I'm guessing the problem is that you  are looking for a mozilla folder in the home directory, but what you need is a .mozilla folder. In linux the . which preceeds the file/foldername makes the file/folder hidden. To see hidden files and holders in nautilus (the file manager) press Ctrl-H (there may also be an option under edit/view but I am on a windows machine and can't check right now). Once you do that you should see a whole bunch of dot files, find the .mozilla one and continue the instructions, once you are done press ctrl+H again to hide the hidden folders.

---

### Post by 2CV67 on 2008-09-08
Thanks ryanhaigh for that post & the previous ones!

I had previously selected "View > Show Hidden Files" (detest terminal...) but hadn't realized it reverted automatically & had to be reset every time I opened the nautilus screen. :oops:

So now I can see .mozilla folder & navigate exactly as you previously said, to ...default/chrome.

No userChrome.css file but now I know to copy userChrome-examples.css & rename it userChrome.css & insert the line:
#PersonalToolbar .toolbarbutton-menu-dropmarker display: none !important; 
& save.
(Just for info: my right-click "Open as Administrator" doesn't work for this & other .css files & fails to find an application, even though a simple double-click opens it fine... so I need to find gksudo nautilus to get any further)

Reboot Firefox - NG
Reboot PC - NG. :(

Then I modified the #PersonalToolbar line by copying the version with {} brackets:#PersonalToolbar .toolbarbutton-menu-dropmarker { display: none !important; }
from old forum thread: [http://ubuntuforums.org/showthread.php?t=732134](http://ubuntuforums.org/showthread.php?t=732134)

Reboot Firefox - Voila!!! :D

I sure wish this had just been a simple clickable option somewhere for us poor GUI-prone users!

Many thanks though for the help on this thread!

---

### Post by 2CV67 on 2008-09-08
Maybe I can try to pull together the instructions for any other GUI-ist who wants to make this change.
Please correct if necessary but keep the whole item together!

**_This needs simplifying - see later post._**

1. Make a launcher for navigating as Root, so you can modify files with Root permissions.
Right click on desktop or panel.
If panel: Select "Add to Panel" "Custom Application Launcher" "Add"
Name "Root" or whatever you want
Command "gksudo nautilus"
"OK"
Should provide a new icon on panel.
Click icon.
Insert your own password (not root password).
Should open navigation window "root – file browser"

2. Navigate to file you need to modify, inside root-filebrowser.
You are probably at "root" showing "desktop".
"View" "Show Hidden Files"
Click "Up" arrow.
Navigate by double-clicking successively "home" "your-username" " .mozilla" "firefox" "blablabla.default" "chrome"

3. If you now see a file "userChrome.css" go straight to item 5.

4. If (probably if you are reading this) you only see a file "userChrome-example.css" then:
Right-click on it & "copy" then right-click beside it & "paste" (or whatever method you prefer for copying a file).
Rename the new file from "userChrome-example (copy).css" to "userChrome.css" (case sensitive...).

5. Open "userChrome.css" by double-click.
Copy-paste the following line into the open file, for example just underneath the block about namespace (probably not critical).
> #PersonalToolbar .toolbarbutton-menu-dropmarker { display: none !important; } 
Save.
Close file browser.
Close Firefox.
Open Firefox.
Should have no more down-arrows on toolbar folders...

Hope that was what you wanted!

---

### Post by ryanhaigh on 2008-09-08
2CV67 you don't need to have nautilus open as root to edit the files in your own home directory such as /home/user/.mozilla etc.

Also (even though it isn't needed) you can probably make using open-as-administrator work by opening the folder as administrator, then right click on the file that won't open, go to properties > open with and add your favorite text editor as the default. Now try openning the file directly with open-as-administrator.

I think this problem must be specific to your GTK theme (remember firefox 3 tries to use icons and themes etc from your native GTK theme) as I do not have this issue at all, the folders have an arrow that fits perfectly with the rest of the theme.

---

### Post by 2CV67 on 2008-09-08
Thanks again ryanhaigh!
> **ryanhaigh said:**
> 2CV67 you don't need to have nautilus open as root to edit the files in your own home directory such as /home/user/.mozilla etc.

:oops: That was a left-over from earlier attempts at finding firefox userChrome in etc/ where I only had read permission.
I will simplify the instructions!

> **ryanhaigh said:**
> Also (even though it isn't needed) you can probably make using open-as-administrator work by opening the folder as administrator, then right click on the file that won't open, go to properties > open with and add your favorite text editor as the default. Now try openning the file directly with open-as-administrator.

When I open the folder as administrator (OK) then the file properties > open-with already says "text editor" selected...
Inside that open folder I can then just plain "open" the file OK (is that as administrator or not?) & don't have the right-click option of "open as admin".
Still unable to open it as admin if I approach from a normally opened folder.

> **ryanhaigh said:**
> I think this problem must be specific to your GTK theme (remember firefox 3 tries to use icons and themes etc from your native GTK theme) as I do not have this issue at all, the folders have an arrow that fits perfectly with the rest of the theme.

My problem is not the size of the arrows, it's the presence of any arrows, which takes up too much space.
I have 16 folders in the toolbar, each with a name, an icon & an arrow (& each with sub-folders etc etc - I have a lot of bookmarks...).
I don't want to delete the icons as I also have some identifiable icons on the toolbar with no names, to save space...
In a perfect world, I would have just:
The identifiable icons with no names, plus the folders as names with no folder icons or arrows.
Getting rid of the arrows gets me back to the satisfactory (but not ideal) situation I am in under XP and was in under Edgy, Fiesty & Gutsy!

I really appreciate your help & patience here & of course the original problem is now solved!

---

### Post by 2CV67 on 2008-09-08
Instructions for any other GUI-ist who wants to make this change. (simplified version, thanks to ryanhaigh...)
Please correct if necessary but keep the whole item together!

1. Navigate to file you need to modify, inside filebrowser.
Places > Home Folder
View > Show Hidden Files
Navigate by double-clicking successively > .mozilla > firefox > blablabla.default > chrome

2. If you now see a file "userChrome.css" go straight to item 4.

3. If (probably if you are reading this) you only see a file "userChrome-example.css" then:
Right-click on it & "copy" then right-click beside it & "paste" (or whatever method you prefer for copying a file).
Rename the new file from "userChrome-example (copy).css" to "userChrome.css" (case sensitive...).

4. Open "userChrome.css" by double-click.
Copy-paste the following line into the open file, for example just underneath the block about namespace (probably not critical).
> #PersonalToolbar .toolbarbutton-menu-dropmarker { display: none !important; }
Save.
Close file browser.
Close Firefox.
Open Firefox.
Should have no more down-arrows on toolbar folders...

Hope that was what you wanted!

---

### Post by 2CV67 on 2008-09-12
Trying to synchronize bookmarks between dual-boot XP & Hardy, I found several on-line solutions which don't appeal much.

I also found this local solution which I am just playing with:
> [http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/](http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/)

Basically it makes Ubuntu FIrefox use the XP Firefox profile, including bookmarks & all the rest.

Anybody trying this, I would advise not deleting your default profile!

Also, you need to have the XP partition mounted before using that profile.

So far, so good!

Basically it works.

Small snag is that I now have the famous arrows back!

Any suggestions as to how I can get rid of them again?

There is no sign of the XP profile in Ubuntu's .mozilla folder, at least not in my home.

I did look in the XP /media/disk/Documents and Settings/me/Application Data/Mozilla/Firefox/Profiles/blablabla.default/Chrome folder but it is empty.

Should I try copying something in there (in XP???) or somewhere else or just give in?

Thanks for any help!

I will probably start another thread on this bookmark sharing if/when I can get past the arrows problem in this thread...

---

### Post by 2CV67 on 2008-09-12
SOLVED! :cool:

I just copied the userChrome.css file from the Ubuntu .mozilla folder to the XP /media/disk/Documents and Settings/me/Application Data/Mozilla/Firefox/Profiles/blablabla.default/Chrome folder

Worked first time!

:D

---

