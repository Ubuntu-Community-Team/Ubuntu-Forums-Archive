---
title: "how to make alert button that pops up on Desktop?"
date: 2008-11-20
forum: General Help
---

### Post by quixote on 2008-11-20
Anacron runs a reminder script.  When it does, I want a nice red button to appear on the desktop. But I can't find a command line way to associate a specific icon with a desktop link.   The longer version of the problem is this:

I have backups scheduled via anacron.  However, even with the time delay, as often as not, it's trying to run them at bad times.  So I thought a clever solution would be for anacron to just run a reminder script.  The reminder would pop up a red button on the desktop and be a link to the actual rsync backup script. So what anacron runs is this:
```
ln -s /home/quixote/backup.sh /home/quixote/Desktop/backup.sh
```
Clicking on that runs the backup shell script.  But the link on the desktop is just the bland little thing for that mimetype, and I don't want to change that.  I.e. I don't want all shellscript files to have a red button icon.

Also, once clicked, I want the icon to disappear until the next time anacron runs the reminder.  I haven't figured out how to do that at all! :(

Is there a way to tell "ln" which icon to use?  Or is there a completely different and better way to do a desktop alert button that links to a shell script?

[This duplicates a question to the Desktop Effects and Customization forum.  I thought that was the right place for it, but there weren't any responses, so then I thought maybe not...?]

---

### Post by pytheas22 on 2008-11-20
I've never done this, but it's an interesting question so I did some poking around.

What I noticed is that if you create a launcher icon in Gnome--i.e. by right-clicking and selecting 'Create Launcher'--what it actually generates is just a text file containing information about which icon the launcher should use, which command it runs, etc.  For example, I created an icon on my desktop called 'edit-some-text', which launches the command 'gedit'.  If I type 'cat ~/Desktop/hey.desktop', this is what I get:

```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gnome-panel-launcher
Name[en_US]=edit-some-text
Exec=gedit
Name=edit-some-text
Icon=gnome-panel-launcher
```

So I'm thinking that basically you could do what you want by following these steps:

1. create a custom launcher.  Set the command that it runs as your backup script, and set the icon to whatever you want it to be.  Store this launcher somewhere other than your desktop, e.g. your /home folder.

2. have anacron copy that launcher to your desktop at the intervals that you want

3. have your backup script delete the launcher from your desktop when the backups finish, so that the icon isn't always on your desktop

I haven't actually done this, but it seems like it would work.  Let me know if something doesn't make sense.

---

### Post by quixote on 2008-11-20
Thanks!  That looks logical.  I'll try it soonest, and report back about results.

About how to get rid of the launcher after the script runs . . . why didn't I think of that! :D

---

