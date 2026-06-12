---
title: "Vista CHKDSK after Kubuntu install"
date: 2008-10-23
forum: General Help
---

### Post by undertow5 on 2008-10-23
Hi,

I have set up my laptop to dual boot windows vista and Kubuntu, with kubuntu installed on a new partion, now whenever i attempt to load Vista from Grub, Vista loads CHKDSK which then proceeds to come to a complete stop at 4%. I have had this problem when I have installed other distributions such as ubuntu, mandriva and opensuse.
I have a suspicion that it might be something to do with CHKDSK not liking linux partitions.
Any help with this would be much appreciated.

---

### Post by caljohnsmith on 2008-10-24
Do you have a Vista Install CD? If not, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). I would recommend running chkdsk from the command line of the CD, and see what errors it reports for your Vista partition:
```
chkdsk /r
```
Or if you use the "map" command to see a list of your drives, you can always run chkdsk with:
```
chkdsk /r C:
```
And replace C with your Vista drive letter if it is different. Anyway, let me know what that returns. :)

---

### Post by undertow5 on 2008-10-24
Thanks for putting me on to the link for the vista recovery disk. Just used the start up repair tool and that seemed to fix it.

---

### Post by caljohnsmith on 2008-10-25
Glad you got Vista working without much trouble and that the Recovery CD helped you; cheers and have fun. :)

---

