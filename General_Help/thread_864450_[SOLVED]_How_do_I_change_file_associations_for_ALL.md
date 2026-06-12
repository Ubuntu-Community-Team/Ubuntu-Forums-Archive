---
title: "[SOLVED] How do I change file associations for ALL programs?"
date: 2008-07-19
forum: General Help
---

### Post by Ekeluo on 2008-07-19
Just as the title asks, is there a way to change system-wide fie associations so I control what programs AWN, gnome-main-menu, beagle, etc open my files with? It's kind of annoying for AWN to open all my video files in Avidemux and other such doings. I use these other methods a lot and would like them to obey nautilus's selections. Is this possible?

Also, how do I allow every program I run to (potential) write to ntfs drives (not sure if it's only ntfs or all other mounted drives that are under /media/)?. I's kind of annoying to have t switch to windows to edit the tags of my music after spotting something.

---

### Post by benste on 2008-07-19
I asked the same question here earlier

I was asked to use "open with" on one file of this type and use custom command than all .ods files were linked to OpenOffice3 for example

---

### Post by silkstone on 2008-07-19
System > Preferences > Preferred Applications deals with some types.

Otherwise, right click on a file whose association you want to change, click on the Open With tab and select an application. That will change the association for all files of that type.

Regarding writing to ntfs drives, I've not tried to do this, but you may have to install ntfs-config with Synaptic.

---

### Post by benste on 2008-07-19
Prefered applications doesn't allow to switch all file type (like xls or docx).
What problem writing to NTFS partitions?

I own a vaio with recovery partition and vista - and it's no problem to read and write into the windowx partitions.

---

### Post by Ekeluo on 2008-07-19
I already configured nautilus and it works well. trouble is sometimes I can't be bothered and I use avant window navigator or recently opened documents and they don't respect nautilus settings.

---

### Post by CatKiller on 2008-07-19
If you pick a file of the type you want to change, right-click and select Properties (NOT Open With...) and then select the Open With tab, you'll see that you can fill the radio button next to the application you want to use. This will set the default application for all files of that type. This definitely works with the Places -> Recent Documents menu; I don't know about AWN since I only use that for application launchers.

To be able to write to an NTFS partition you need to have mounted it using ntfs-3g. You'll also need to have appropriate settings in your /etc/fstab. There is a wealth of detailed information about how to do that on this forum and in the Ubuntu Guide.

---

### Post by Ekeluo on 2008-07-20
I've configured nautilus to behave the way I want, and I'm fine with it. The problem is with other programs like beagle and awn (stacks plugger, file browser plugins). Where exactly do they get file association from?
On the ntfs writing issue, nautilus can do that too (copy cut delete, the lot). But Quod Libet, Amarok, easytag and banshee can't write tags to my music on the ntfs partition. They read them fine but give permission errors when trying to write tag changes. Once I move the file to my home partition it writes without problem. How do I fix this?

P.S. Also (another gnome problem) what is is with GNOME trash handling? why do awn and gthumb use a different trash can from nautilus and the rest of my pc?
Where is the consistency?

---

### Post by chochem on 2008-07-25
There is more information about file type associations in Gnome (and associates, like Xfce) in the thread [here]("http://ubuntuforums.org/showthread.php?t=51012").

---

### Post by Ekeluo on 2008-12-28
chochem, thanks 4 ur link, gave me a foolproof (though lengthy) method of fixing the choices. AWN respects those. Thanx (sorry can't seem to find the button, so THANKS AGAIN:-)).

---

