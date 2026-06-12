---
title: "gedit not responding in 8.10"
date: 2008-11-04
forum: General Help
---

### Post by chunchengch on 2008-11-04
All the text files can not be opened with mouse click, and neither with command 'gedit' in terminal, I have to open files with 'sudo gedit' command, why does this happen?

Thanks for any clue or solution.

---

### Post by chunchengch on 2008-11-04
No one has this problem?

---

### Post by Andreas1 on 2008-11-05
i have a similar problem since 8.10

when i try to run gedit (or gksudo gedit) it takes 20 seconds of 100% cpu usage until gedit appears.

---

### Post by bapoumba on 2008-11-05
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/276094](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/276094)
[https://bugs.launchpad.net/ubuntu/+source/human-theme/+bug/252399](https://bugs.launchpad.net/ubuntu/+source/human-theme/+bug/252399)
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/280411](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/280411)

Several bug are lying around. Try to change your icon theme, or plugins :)

---

### Post by chunchengch on 2008-11-05
bapoumba,

Thanks a lot!

The "File Browser Pane" plugin causes gedit to be abnormal, the problem is solved by unchecking this plugin, thanks again.

---

### Post by Spike-X on 2008-11-06
> **chunchengch said:**
> 
The "File Browser Pane" plugin causes gedit to be abnormal, 

Where would I find this?

---

### Post by Spike-X on 2008-11-06
Never mind, I found it!

It's in gedit, under Edit > Preferences > Plugins.

---

### Post by wgrant on 2008-11-06
A fix for the File Browser Pane bug is currently in testing, and should be available within a week.

---

### Post by Spike-X on 2008-11-06
Good to hear. Thanks William (Will? Bill? Billy? Grantie?).

---

### Post by Forcasted_Underdog on 2008-11-11
Just another great example of the Ubuntu community coming through.  Great fix.

---

