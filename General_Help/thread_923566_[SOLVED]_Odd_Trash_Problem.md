---
title: "[SOLVED] Odd Trash Problem"
date: 2008-09-18
forum: General Help
---

### Post by psuliin on 2008-09-18
I'm running Hardy, and I've gotten a strange problem with my trash.  A file that I deleted (that is, moved to the trash) seems to have gotten its permissions bollixed, and now when I try to empty the trash that file always remains behind.  I've even tried the "delete from trash" menu item, but it just gives me a permission error. 

The odd thing is that when I try to move it out of the trash I also get a permission error.  So this must have happened somehow AFTER I moved it to the trash.  

I'd use chmod to change the permissions, but I can't seem to cd to my trash - possibly I just don't know the right command.  

So, any suggestions?

---

### Post by drs305 on 2008-09-18
The answer will probably be found in the Trash link in my signature line. Most likely there is some root-owned trash in the bin that you as a normal user can't delete.

Most likely you can open nautilus with administrator privileges to delete it:
```
gksu nautilus
```

In Hardy:
Normal trash is located at ~/.local/share/Trash
Root trash is located at /root/.local/share/Trash

Refer to the link for a whole array of information about trash bins and how to find and delete trash from your system.

---

### Post by psuliin on 2008-12-29
Well, as it turned out the problem was a directory in my normal trash that was owned by root.  How I managed to put it in the trash in the first place I can't tell you.  But I used the pathway you gave to get to my "normal" trash and then used 

```
sudo chown -R --no-preserve-root
```

to take ownership of the directory and all contents.  Even then though I had to drill down to the bottommost level of the directory and delete the files and subdirectories in each level on my way back up.  

Major nuisance, but it's fixed now.

---

