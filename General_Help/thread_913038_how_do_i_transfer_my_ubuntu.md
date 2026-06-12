---
title: "how do i transfer my ubuntu"
date: 2008-09-07
forum: General Help
---

### Post by washable mist on 2008-09-07
i want to move my ubuntu 8.10 installaion from a 40gb hard drive to a new 500gb hard drive, i don't want to have to re-install because i have everything just the way i want it, how can i do this

---

### Post by schauerlich on 2008-09-07
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

Look under the "Backing up whole installation" heading.

I would use dd_rescue. The command would look something like this:

```

dd_rescue /dev/hda1 /dev/sda1

```

Where /dev/hda1 is the path to your 40gb HD and /dev/sda1 is the path to your 500gb HD. Be SURE that you copy **from** your 40gb and **to** your 500gb HDs, or else you might copy a blank drive over your Ubuntu installation, leaving you with nothing.

---

### Post by IanW on 2008-09-07
WARNING! Be _very_ sure you have set those paths mentioned above correctly!

Get them backwards and you'll copy a blank drive all over your Ubuntu install!

(Voice of experience speaking here)](*,)

---

### Post by Sycron on 2008-09-07
> **IanW said:**
> Voice of experience speaking here](*,)

:lolflag:

---

### Post by schauerlich on 2008-09-07
> **IanW said:**
> WARNING! Be _very_ sure you have set those paths mentioned above correctly!

Get them backwards and you'll copy a blank drive all over your Ubuntu install!

(Voice of experience speaking here)](*,)

I put a warning in there, in case someone decided not to read the whole thread. :)

---

