---
title: "Where is &quot;Hardware Information&quot; in Hardy?"
date: 2008-06-15
forum: Hardware
---

### Post by stanley45 on 2008-06-15
I switched over to Hardy some time ago and everything worked fine.  But now I have no internet.  It appears I have no wireless hardware associated with the machine anymore...  I am trying to follow the troubleshooting guide, and it says go to System->Preferences->Hardware Information.  That's where it is in Gutsy.  But it's not there on my Hardy.  Nor can I find anyway to add it to the Preferences list - it simply doesn't appear anywhere.

Can anybody help me take the first troubleshooting step?

---

### Post by sdennie on 2008-06-15
That application was called hal-device-manager.  I have no idea where it went in Hardy (it was really useful) but, you can get similar functionality by installing gnome-device-manager.  

```

sudo apt-get install gnome-device-manager

```

After installing it, it will bein Applications->System Tools->Device Manager.  Go to View->Device Properties and the functionality should be very similar to what you saw in Gutsy.

---

### Post by stanley45 on 2008-06-15
Thank you very much, but apt needs to access the internet, and I can't.

---

### Post by sdennie on 2008-06-15
In that case you can use lshw:

```

sudo lshw

```

Or, easier to read:

```

sudo lshw -html > hardware.html

```

The latter will give you a file called hardware.html that can be opened in a browser and gives information similar to hal-device-manager.

---

### Post by Nessa on 2008-06-15
vor, that is very useful information. Thank you. :p

---

