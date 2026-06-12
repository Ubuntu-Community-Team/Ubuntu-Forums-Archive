---
title: "update manager"
date: 2008-11-01
forum: General Help
---

### Post by buzzforb on 2008-11-01
was trying to download automatix2 before realizing i could not do so on 8.04 nad got this message as a result. How do i deal with this.

"'E:Type 'http://www.getautomatix.com/keys/automatix2.key' is not known on line 16 in source list /etc/apt/sources.list, E:The list of sources could not be read"

---

### Post by jpeddicord on 2008-11-01
Automatix is not supported here, and was discontinued for Ubuntu. Consider installing the [ubuntu-restricted-extras]("apt:ubuntu-restricted-extras") package instead for non-free codecs, Flash, fonts, and Java.

---

### Post by knutschr on 2008-11-01
You should really not use automatix2!
That can screw your whole system.
You can do everything from Synaptic instead, safe.

---

### Post by buzzforb on 2008-11-01
I am aware of not being able to use automatix without screwing up my system, bit it appears this is what has happened. how do i remove this command line so that this error does not prevent me from using my synaptic update manager?

---

### Post by jpeddicord on 2008-11-01
> **buzzforb said:**
> I am aware of not being able to use automatix without screwing up my system, bit it appears this is what has happened. how do i remove this command line so that this error does not prevent me from using my synaptic update manager?

Open System > Preferences > Software Sources, and on the Third-party tab, disable the source that points to that URL in that error.

---

### Post by buzzforb on 2008-11-01
i do not have that as an option

---

### Post by jpeddicord on 2008-11-01
> **buzzforb said:**
> i do not have that as an option

Ack, sorry, System > Administration > Software Sources.

See attachment.

---

