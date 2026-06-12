---
title: "places menu won't open home folder, desktop, tries to open google earth"
date: 2008-10-30
forum: General Help
---

### Post by uschxc on 2008-10-30
whenever i try to goto Places in the top menu, the Home Folder and Desktop icons, as well as any favorites I might add in Nautilus, opens google earth.  now that i've removed google earth i get this error

"Could not location 'file:///home/user'"

"Failed to execute child process /opt/google-earth//googleearth"

i think this is happened to me once before but i can't remember what the fix was.  anyone have any ideas?

---

### Post by fooman on 2008-10-30
yeah, its happened to me before also,  only i had /home trying to open with xine.

not sure how i fixed it,  but try this:

go to places > computer

in the left hand column,  click on your user name,  then in the right hand side, *right*-click on "desktop"...choose "properties" from the menu.  in the properties box,  click the "open with" tab.

make sure "open folder" is selected.  close the box and see if thats the fix.

---

### Post by hophead929 on 2008-11-01
> **fooman said:**
> yeah, its happened to me before also,  only i had /home trying to open with xine.

not sure how i fixed it,  but try this:

go to places > computer

in the left hand column,  click on your user name,  then in the right hand side, *right*-click on "desktop"...choose "properties" from the menu.  in the properties box,  click the "open with" tab.

make sure "open folder" is selected.  close the box and see if thats the fix.

Archive Manager was selected. Once I changed it to Open Folder, the shortucts from Places worked again. Thanks!

---

### Post by raucous on 2008-11-04
great!

thanks.

---

### Post by nmcgrew on 2010-01-17
Documents won't open for me.  Music, Pictures, Videos, File System, Desktop and Home all open fine but Documents does nothing.  Ubuntu/9.10 (karmic)  Help? :(

---

### Post by Arun_Chandranath on 2010-02-04
I faced the same problem in Ubuntu 9.10. For me, places menu were opening up mplayer. I tried changing the 'Open with' under the properties tab, but that didnt help. Finally, this is how I got my places menu working again:

You need to check the contents of the .local/share/applications/mimeapps.list file

$ cat .local/share/applications/mimeapps.list
[Added Associations]
text/html=epiphany.desktop;firefox.desktop;
application/x-executable=userapp-bless-QAFMEU.desktop;
application/x-extension-Ora=gnochm.desktop;
application/x-extension-Orb=gnochm.desktop;
application/x-extension-Pra=gnochm.desktop;
application/octet-stream=gnochm.desktop;
application/x-extension-Hig=gnochm.desktop;
application/vnd.rn-realmedia=realplay.desktop;
text/x-csharp=gedit.desktop;
[COLOR=Red]**inode/directory=mplayer.desktop;**[/COLOR]

Issue was fixed by editing .local/share/applications/mimeapps.list
and changing :
[COLOR=Red]**inode/directory=mplayer.desktop;**[/COLOR]
to[COLOR=Lime][B]
[COLOR=Red]inode/directory=nautilus-folder-handler.desktop;[/COLOR][/B][/COLOR]

Hope this helps.

Thankyou
Arun

---

### Post by dr_dred5 on 2010-04-04
Thanks Arun, that fixed it for me in Jaunty.

Cheers!

---

### Post by Sodear on 2010-05-26
> **Arun_Chandranath said:**
> I faced the same problem in Ubuntu 9.10. For me, places menu were opening up mplayer. I tried changing the 'Open with' under the properties tab, but that didnt help. Finally, this is how I got my places menu working again:

You need to check the contents of the .local/share/applications/mimeapps.list file

$ cat .local/share/applications/mimeapps.list
[Added Associations]
text/html=epiphany.desktop;firefox.desktop;
application/x-executable=userapp-bless-QAFMEU.desktop;
application/x-extension-Ora=gnochm.desktop;
application/x-extension-Orb=gnochm.desktop;
application/x-extension-Pra=gnochm.desktop;
application/octet-stream=gnochm.desktop;
application/x-extension-Hig=gnochm.desktop;
application/vnd.rn-realmedia=realplay.desktop;
text/x-csharp=gedit.desktop;
[COLOR=Red]**inode/directory=mplayer.desktop;**[/COLOR]

Issue was fixed by editing .local/share/applications/mimeapps.list
and changing :
[COLOR=Red]**inode/directory=mplayer.desktop;**[/COLOR]
to[COLOR=Lime][B]
[COLOR=Red]inode/directory=nautilus-folder-handler.desktop;[/COLOR][/B][/COLOR]

Hope this helps.

Thankyou
Arun
In my case the mimeapps.list shows inode/directory=rhythmbox.desktop; nautilus-folder-handler.desktop.
I tried to edit using gksudo gedit  to edit the list and remove the reference to rhythmbox but had no luck though I did save in the new edit window.
Evidently I am missing something and don't quite know how to edit.  Can you help please.

---

### Post by Sodear on 2010-05-27
Thank you Arun.  This solved the problem for me.
I was able to edit the mimeapps.list by locating the file in ~/.local/share/applications (show hidden files) and opening it. After that Places worked properly.  In my case the incorrect line was: inode/directory=rhythmbox.desktop; nautilus-folder-handler.desktop
I just deleted the line and entered inode/directory=nautilus-folder-handler.desktop.
Sudhir

---

### Post by aygunmur on 2010-09-25
fooman tnx. thats fixed it.

---

### Post by cogier on 2011-02-27
Sodear,

You are a star. This worked a treat.

---

