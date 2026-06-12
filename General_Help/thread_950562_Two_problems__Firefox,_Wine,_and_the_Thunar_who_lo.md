---
title: "Two problems:  Firefox, Wine, and the Thunar who loves them."
date: 2008-10-17
forum: General Help
---

### Post by Minguo on 2008-10-17
Hi, I've got two weird problems maybe they're related?

1.) Firefox - After downloading files in Firefox, if I open the 'downloads' page and select 'open containing folder', that doesn't work.

At first, I would get an error saying basically that there was no program associated with the file type or somesuch, and a dialog to select an appropriate program.

I followed the steps in this solution.

[http://rubylution.ping.de/articles/2007/09/11/open-containing-folder-in-firefox-under-linux](http://rubylution.ping.de/articles/2007/09/11/open-containing-folder-in-firefox-under-linux)

and now, nothing happens.  No error, and no folder```

```.



2.)  Wine - I've installed it, but whenever I open the 'Browse C drive' menu item, it refuses to work.  At first  it would throw this error.

```
Failed to open URL "~/.wine/drive_c:".
The URL "~/.wine/drive_c:" is not supported.
```

Ok, did some googling and forumsearching and found threads like this one.
[http://ubuntuforums.org/showthread.php?t=762074](http://ubuntuforums.org/showthread.php?t=762074)

and bugs like this one.

[https://bugs.edge.launchpad.net/ubuntu/+source/wine/+bug/223989](https://bugs.edge.launchpad.net/ubuntu/+source/wine/+bug/223989)

I changed the shortcut entry as directed (first to 
```
xdg-open ~/.wine/dosdevices/c:
```
and then to
```
thunar ~/.wine/dosdevices/c:
```

Then I tried both methods using complete paths. /home/user_name/.wine/. . . instead of ~/.wine. . .

Everything I've tried here works if I type it into terminal.  however, NOTHING works if I try to run it from the shortcut.

Anything with a ~/.wine prefix gives me a "~/.wine/drive_c" is not supported error, anything with a /home/user_name/ prefix doesn't do anything at all.  No error, and no folder.

One of these solutions seems to have worked for everybody else asking the question.   What's going on?

I have attached a screenshot of my FF about:config and the pertinent wine shortcut config file to show how it is currently.

---

### Post by Minguo on 2008-10-17
Ok, so one more problem.

If I run Catfish (file search program) and search for a folder or file,  I can open files just fine from within the Catfish GUI, howeverif I select 'jump to' or try to 'open' a folder, I get

```
Error: Could Not open the file 'path of folder'
```

Thunar appears to be borked.

---

