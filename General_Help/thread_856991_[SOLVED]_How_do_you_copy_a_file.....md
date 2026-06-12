---
title: "[SOLVED] How do you copy a file...."
date: 2008-07-12
forum: General Help
---

### Post by Redptc on 2008-07-12
I downloaded 'sql-ledger' in the hope of having an accounting system that was not Windows dependent. All went smoothly, downloaded easily and simply but I have no idea were to go from here!

I need to copy a file from one location to another. I don't know the terminal command, probably, CP or similar. I don't think it is possible to 'drag and drop'.

Can someone give me the terminal requirements to copy a file from one location to another? I am not a 'nerd' and don't think i ever will be, so basic help would be appreciated. Thanks!

---

### Post by iaculallad on 2008-07-12
By using the cp terminal command:

Say we are to copy menu.lst file to user's home directory:

> cp source destination

I.E:

```
cp /boot/grub/menu.lst ~/Documents
```

or

```
cp /boot/grub/menu.lst /home/username/Documents
```

You may need sudo when copying files to restricted locations.

---

### Post by VMC on 2008-07-12
> **Redptc said:**
> I downloaded 'sql-ledger' in the hope of having an accounting system that was not Windows dependent. All went smoothly, downloaded easily and simply but I have no idea were to go from here!

I need to copy a file from one location to another. I don't know the terminal command, probably, CP or similar. I don't think it is possible to 'drag and drop'.

Can someone give me the terminal requirements to copy a file from one location to another? I am not a 'nerd' and don't think i ever will be, so basic help would be appreciated. Thanks!

Yes you can drag and drop. But from a Terminal it's this

'cp /somedir /toanotherdir' . If there is subdirectories involved then us the -R option. It's best to read up on the manual. From the same Terminal type 'man cp'.

You can use Nautilus for the gui drag&drop.

---

### Post by jonlemur on 2008-07-12
You should also be able to do it graphically by running ```
gksu nautilus
```from the command line and navigating to the folder where you downloaded the file.  You can copy and move it anywhere then just by navigating in the file browser.  If you don't need root privileges (if everything is being copied to somewhere in your home directory) you can leave off the 'gksu'  That command gives you the privileges to write to folders other than your home directory.

EDIT: Oh, now I see that VMC already suggested that.  Oops.

---

### Post by Redptc on 2008-07-12
Thanks everybody, that got me to the next step.

I just wanted a 'bean-counter' so I didn't figure on all this extra 'stuff'.

I will probably be back here soon! Appreciate the rapid response.

---

