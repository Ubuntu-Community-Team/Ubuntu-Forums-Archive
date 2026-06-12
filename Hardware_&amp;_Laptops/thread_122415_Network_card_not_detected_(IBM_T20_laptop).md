---
title: "Network card not detected (IBM T20 laptop)"
date: 2006-01-27
forum: Hardware &amp; Laptops
---

### Post by Monkee on 2006-01-27
when i installed Ubuntu it said it couldn't detect my network card. i was previously using red hat 9 which picked it up fine. i am completely new t linux tho and seeing as i had no clue how to fix it i switched to suse 10, where i encountered other (completely different) problems so i have to fix one of these. What should i do?

---

### Post by mips on 2006-01-28
Try turning apci or apic of during bootup and see what happens.

---

### Post by Skye on 2006-01-28
After some googling, I found that the IBM T20 uses the Intel Pro/100+ series network chipset, which should definitely be supported.  Assuming you can log in to Gnome, try the following in a terminal:

```

sudo insmod eepro100.o

```

If that completes successfully, go to networking (System -> Administration -> Networking) and set up your network as needed.

If it doesn't work, we can try something else.

---

### Post by r4ik on 2006-01-28
I am trying the same thing here.
Output,
insmod: can't read 'eepro100.o' No such file or directory.
Any other suggestions please ?

---

### Post by r4ik on 2006-01-28
lspci ; lspci -n  output showed it is a 3Com 3c556b in my case
and i think most T20's have one.
Anyway there is a shipload on the topic (Google) mostly all unsolved.
Havent read them all :)
I am going for the drivers see if i can find them.
If there is anyone with a shortcut please let me know.

Right once i get them i am going to put them......
Little bit difficult downloading without connection ay Einstein.

---

### Post by Skye on 2006-01-28
Sorry, my bad-  I guess I didn't go into enough depth with google.

The page here: ([http://www.thinkwiki.org/wiki/3Com_10/100_Ethernet_Mini-PCI_Adapter_with_56K_Modem](http://www.thinkwiki.org/wiki/3Com_10/100_Ethernet_Mini-PCI_Adapter_with_56K_Modem)) looks like it may help.  Thinkwiki is a wonderful resource for thinpad owners who run linux.

If you eventually do find drivers, have a windows partition on the same machine, and you're using the ext2 or ext3 filesystem in linux, I believe there are tools to write to linux from windows, so you can transfer the files that way.

Google pops up [http://www.fs-driver.org/]("http://www.fs-driver.org/"), I'm sure there are more.

Also, you could just burn a CD/make a floppy/use a USB disk.

I hope this helps!

---

### Post by r4ik on 2006-01-29
Thanks fot youre reply i found parts of it but yours seems to be more complete.
I am going for it now.
Thanks agian will keep you informed.

---

### Post by r4ik on 2006-01-29
Did not succeed and it has to be back monday.
Wacked another dist. on it.
My bad.
Promised to let you know.

---

### Post by Skye on 2006-01-29
I'm sorry to hear that.  In the interests of posterity, what problems did you run in to?

---

### Post by r4ik on 2006-01-30
I am not gonna make up story's here it was the dead-line and most of all
lazyness.
I took the easy way out if it was mine things might have been different.
Thanks for pionting me the way next time with more time (hopefully)
i will dig deeper.
Like to know if you succeeded i hope you did.

---

