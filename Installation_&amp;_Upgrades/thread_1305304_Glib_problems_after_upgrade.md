---
title: "Glib problems after upgrade"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by fenixk19 on 2009-10-29
Hello. I've upgraded to karmic, but i got very strange problem. I haven't seen it anywhere else. Lots of applications(even X server) don't start, because of broken libgobject*.so. For example, here is from kdm.log:
```

/usr/lib/kde4/libexec/kdm_greet: symbol lookup error: /usr/lib/libgobject-2.0.so.0: undefined symbol: g_array_ref

```
And most of apps points to this g_array_ref. I downgraded package libglib2.0-0 to jaunty version, and it works better, but points to some other errors in some apps. At least, X works. But with such replacement, i can't use dpkg, because it dislikes version of glib. I'm sure it is ubuntu bug, but i don't understand, why it is only me, who have it.

I'm using x64 version.

---

### Post by fenixk19 on 2009-10-30
Up this topic. I need help!

---

### Post by fenixk19 on 2009-10-30
Up

---

### Post by fenixk19 on 2009-10-30
Up

---

### Post by AwesomeTux on 2009-11-03
I am also experiencing this, anyone figure it out yet?

---

### Post by fenixk19 on 2009-11-03
I've fixed problem :)
There was an obsolete library, that is loading instead of new one. For me it was something like:
/usr/lib/libglib-2.0.so.0.1502.0

Try to do
```

 ls /usr/lib/libglib* /usr/lib/libgobject*

```
to see what you have.

---

### Post by AwesomeTux on 2009-11-03
Here's what I get...

```
/usr/lib/libglib-2.0.a
/usr/lib/libglib-2.0.la
[B][COLOR="DeepSkyBlue"]/usr/lib/libglib-2.0.so
/usr/lib/libglib-2.0.so.0[/COLOR]
[COLOR="Green"]/usr/lib/libglib-2.0.so.0.2000.4
/usr/lib/libglib-2.0.so.0.2000.5[/COLOR][/B]
**[COLOR="DeepSkyBlue"]/usr/lib/libglibmm-2.4.so.1[/COLOR]**
/usr/lib/libglibmm-2.4.so.1.2.0
**[COLOR="DeepSkyBlue"]/usr/lib/libglibmm_generate_extra_defs-2.4.so.1[/COLOR]**
/usr/lib/libglibmm_generate_extra_defs-2.4.so.1.2.0
/usr/lib/libgobject-2.0.a
/usr/lib/libgobject-2.0.la
[COLOR="DeepSkyBlue"][B]/usr/lib/libgobject-2.0.so
/usr/lib/libgobject-2.0.so.0[/B][/COLOR]
[COLOR="Green"][B]/usr/lib/libgobject-2.0.so.0.2000.4
/usr/lib/libgobject-2.0.so.0.2000.5[/B][/COLOR]
/usr/lib/libgobject-2.0.so.0.2200.2
```

---

### Post by fenixk19 on 2009-11-04
Those files with 2000 in the name seems to be old trash. Try to remove them.
```

sudo rm /usr/lib/libgobject-2.0.so.0.2000.4 /usr/lib/libgobject-2.0.so.0.2000.5 /usr/lib/libglib-2.0.so.0.2000.4 /usr/lib/libglib-2.0.so.0.2000.5
```
Maybe it is better to backup them, but i think it is not needed. And maybe it is better to reinstall libglib2.0-0 package, but it not necessary too.

---

### Post by AwesomeTux on 2009-11-05
> **fenixk19 said:**
> Those files with 2000 in the name seems to be old trash. Try to remove them.
```

sudo rm /usr/lib/libgobject-2.0.so.0.2000.4 /usr/lib/libgobject-2.0.so.0.2000.5 /usr/lib/libglib-2.0.so.0.2000.4 /usr/lib/libglib-2.0.so.0.2000.5
```
Maybe it is better to backup them, but i think it is not needed. And maybe it is better to reinstall libglib2.0-0 package, but it not necessary too.

But '/usr/lib/libgobject-2.0.so' and '/usr/lib/libgobject-2.0.so.0' already link to '/usr/lib/libgobject-2.0.so.0.2200.2', and 'libgobject-2.0.so.0' is the only library file that is loaded.

So it shouldn't matter if the old versions are there, right?

---

### Post by fenixk19 on 2009-11-05
I don't know. The best way is to check it, by removing this files. I'm just telling, what helped me.

---

### Post by AwesomeTux on 2009-11-06
Fixed it!

For some reason 'libglib-2.0.so.0.2200.2' is installed in /lib in Ubuntu 9.10? So I linked '/usr/lib/libglib-2.0.so.0' to '/lib/libglib-2.0.so.0' which links to '/lib/libglib-2.0.so.0.2200.2'

And everything works now! ):P

---

### Post by fenixk19 on 2009-11-06
It's a library mess. Congratulations.

---

### Post by mwq27 on 2009-11-08
How did you link the files together to get it to work?

---

