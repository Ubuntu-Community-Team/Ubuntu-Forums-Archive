---
title: "cant recover from trash"
date: 2008-07-19
forum: General Help
---

### Post by dexter.deepak on 2008-07-19
i just committed a big mistake..my kiddie sister had a tiff with me and she deleted (by right-click-> move to trash) my fav music. i never resisted coz i knew i was going to restore them back from trash.
now i am shocked to see that the files are not there !!:(
i wonder what went wrong and how would i recover them !! is there an "undelete" software for ubuntu ?
i am using ubuntu hardy and the files were on a ntfs drive..could that be the problem ??

need some help ...swear i wont have a fight with my sis ever !!](*,)

---

### Post by Vivaldi Gloria on 2008-07-19
> **dexter.deepak said:**
> i just committed a big mistake..my kiddie sister had a tiff with me and she deleted (by right-click-> move to trash) my fav music. i never resisted coz i knew i was going to restore them back from trash.
now i am shocked to see that the files are not there

Sorry to hear that. Try these in the following order:

1) Look at ~/.local/share/Trash/files. Also look at the top level of the disk the file is deleted from, i.e. if it was in /mnt/mountpoint then go there. Then press ctrl+H to see hidden files. Look in the .trash-* folder.

2) Try rebooting.

3) Try fsck on that disk.

4) If none of the above work then have a look at Photorec. I haven't used it myself so I cannot comment on it.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

