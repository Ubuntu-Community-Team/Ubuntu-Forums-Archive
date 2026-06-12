---
title: "cant edit fstab after reinstall"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by THEBIGEYE on 2007-03-24
[CENTER]i have just reinstalled ubuntu edgy and now have a problem i have never encountered before
i cannot edit the fstab file when i issue the command i get this print out
         ian@ian-desktop:~$ sudo edit /etc/fstab
Warning: unknown mime-type for "/etc/fstab" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
ian@ian-desktop:~$ [/CENTER]
 does any one encountered this before any ideas

---

### Post by chewearn on 2007-03-24
Change edit to gedit, thus: :)
```
sudo gedit /etc/fstab
```

---

### Post by THEBIGEYE on 2007-03-24
thanks for the advice
i tied that not getting messege anymore
 but still not getting actuall file up in editor to edit i have an editor installed do i have to create fstab file because i go to /etc cant find fstab
everything was fine before install 


ian@ian-desktop:~$ sudo gedit /etc/fstab
Password:
ian@ian-desktop:~$ 
 this is the outcome of the command no text editor comes up

---

### Post by chewearn on 2007-03-24
That's strange, you should have a /etc/fstab file.

Try:
```
ls /etc/fstab*
```

DId you see "fstab~"?  This is a backup, might help you restore it.

Else, you will need to recreate it.

---

### Post by THEBIGEYE on 2007-03-24
hello yes its there it 
but it still wont bring up a text editor can i configure it in anyother way?

---

### Post by THEBIGEYE on 2007-03-24
quick up date i can acess it thru the gui but its read only how can i acess it thru gui with root privilages?

---

### Post by kevinlyfellow on 2007-03-24
what happens when you just enter the command gedit?

Things you can try:
 
```
sudo gedit 
``` and then open up /etc/fstab via the gedit interface;

```
sudo vim /etc/fstab
```  You'll need to do some reading for this ;-) [http://arioch.unomaha.edu/~jclark/vim.html](http://arioch.unomaha.edu/~jclark/vim.html);

```
sudo pico /etc/fstab
```

good luck

---

### Post by chewearn on 2007-03-24
Also, can you do this:

First backup the backup, so it is not overwritten by future editing of fstab:
```
sudo cp /etc/fstab~ /etc/fstab.backup
```Then, restore the backup:
```
sudo cp /etc/fstab~ /etc/fstab
```Then, if opening in text editor still gives read only, can you check the file attributes?
```
ls /etc/fstab -l
```

---

