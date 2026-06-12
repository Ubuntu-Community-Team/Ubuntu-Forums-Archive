---
title: "Ecrypt in Ubuntu 8.04"
date: 2008-10-07
forum: General Help
---

### Post by MunkyJunky on 2008-10-07
I noticed earlier that Ibex is coming with an encrypted folder in the home dir. The page I read (Ubuntus 8.10 features page) says:

> Encrypted private directory

The ecryptfs-utils package was recently promoted to Ubuntu main, with support for a secret encrypted folder in your Home Folder (by Michael Halcrow, Dustin Kirkland, and Daniel Baumann).

You can help test this new feature by going to Applications &#8594; Accessories &#8594; Terminal and typing:

    * sudo aptitude install ecryptfs-utils
    * ecryptfs-setup-private


I'm running Hardy 8.04, and the first command worked perfectly, but the second one (ecryptfs-setup-private) just outputs a 'command not found'. 

Anyone else tried installing this and had a success? Or anyone able to point me in the right direction to getting this fixed?

---

### Post by g33k on 2008-10-08
I am interested in this as well.  Have you tried installing from source?

---

### Post by nathanieldelaney on 2008-10-17
I was also interested in this, and found a utility called cryptkeeper. It's in the repositories, listed on Synaptic under "System Administration (Universe)". I was able set up an encrypted folder pretty easily.  I tried a lot of the other encryption tools but they weren't nearly as easy to use as cryptkeeper. You can use Synaptic or:

sudo aptitude install cryptkeeper

Once installed, it appears on the gnome menu under Applications - System Tools. Once you launch the program, a key icon appears on the taskbar. Click that and select "New Encrypted Folder." The rest seems self explanatory.

---

### Post by MunkyJunky on 2008-10-18
Cryptkeeper is a great solution! Thanks that posting it up ;)

---

### Post by meho_r on 2008-10-18
But a little bit limited. Maybe to have a look at "plain" encfs.

Basics are:

1. Create encrypted folder as well as the folder in which it will be mounted (in the example provided below you should change paths and names as desired; I chose **test-encrypted** and **test-decrypted** just to point out which folder will be containing encrypted data and which decrypted ones)

```
encfs \tmp\test-encrypted \tmp\test-decrypted

```

2. Follow the instructions.

3. After creation, the encrypted folder will be mounted as virtual drive (in fact, that virtual drive will be **test-decrypted** folder) which you use to store and manipulate data.

4. To unmount the virtual drive type in:
```
fusermount -u \tmp\test-decrypted
```

This approach is especially useful if you're using [dropbox](https://www.getdropbox.com) and want your data stored in encrypted form.

---

