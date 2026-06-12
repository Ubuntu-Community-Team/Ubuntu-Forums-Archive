---
title: "How to add a 'extra repository' to my system???"
date: 2008-11-19
forum: General Help
---

### Post by three_jeeps on 2008-11-19
Hi:
I need to get and install a program that is maintained by a person with their own website and repository.

I was told to I need to add the following repository to my system:

deb [http://code.high.com/apt/foo_v_4.2](http://code.high.com/apt/foo_v_4.2)
or maybe it was:
.deb [http://code.high.com/apt/foo_v_4.2](http://code.high.com/apt/foo_v_4.2)

(it was typed two different ways)

How do I do this with either apt or aptitude?

The person indicated that I should add the 'extra repository' a certain way so that upgrades would happen automatically.  How do I do this?

thank much for your help.

-John

---

### Post by snowpine on 2008-11-19
Hi Three Jeeps,

Your repositories are controlled by the /etc/apt/sources.list file. The following terminal command will open the file for editing so you can add that line (I think it probably does not start with a period; the first version looks correct).

```
gksu gedit /etc/apt/sources.list
```

Good luck!

---

### Post by rampageoberon on 2008-11-19
You can add it to your /etc/apt/sources.list file.

and then do the following to update it ```
sudo aptitude update
```

This assumes you have the repository name correctly

example would be:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

---

### Post by taurus on 2008-11-19
Open a terminal and edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and add this line to the end of it.

```
deb http://code.high.com/apt/foo_v_4.2
```
Save it and close down the gedit editing window.  Then run

```
sudo apt-get update
```

---

### Post by kostkon on 2008-11-19
> **three_jeeps said:**
> Hi:
I need to get and install a program that is maintained by a person with their own website and repository.

I was told to I need to add the following repository to my system:

deb [http://code.high.com/apt/foo_v_4.2](http://code.high.com/apt/foo_v_4.2)
or maybe it was:
.deb [http://code.high.com/apt/foo_v_4.2](http://code.high.com/apt/foo_v_4.2)

(it was typed two different ways)

How do I do this with either apt or aptitude?

The person indicated that I should add the 'extra repository' a certain way so that upgrades would happen automatically.  How do I do this?

thank much for your help.

-John
The previous posters assumed wrongly that you are an advanced user like them.

I'll show you the easy way. Go to *System &#8594; Administration &#8594; Software Sources* and in the* Third-Party Software* tab press the *Add* button and add the line for the repository you want to add in the field that will appear, that is
```
deb [http://code.high.com/apt/foo_v_4.2](http://code.high.com/apt/foo_v_4.2)
```
then press *Close* and then *Reload*.

If everything goes fine and your repo url is right, the window will close, otherwise an appropriate error will appear.

---

### Post by Vadi on 2008-11-19
I'll second kostkon. See his instructions of the official help file: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by three_jeeps on 2008-11-19
> **Vadi said:**
> I'll second kostkon. See his instructions of the official help file: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Thank you ALL very much!  I forgot to mention that I am running a headless server (8.04), because I want to keep the disk space down, not to mention I am more comfortable with the cl.  
In any case, all of the posts here helped, and I most appreciate the pointer to the doc...both GUI and CL versions were helpful and informative! I did manage to grab the application, after a side track of figuring out how to point to a keyserver....(another story )...

-J

---

