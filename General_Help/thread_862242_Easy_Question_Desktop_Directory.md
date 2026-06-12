---
title: "Easy Question: Desktop Directory?"
date: 2008-07-17
forum: General Help
---

### Post by lupinesoul on 2008-07-17
What is the desktop directory in Ubuntu?

---

### Post by jonian_g on 2008-07-17
it is /home/usermane/Desktop

Click Places>Desktop and you are there

---

### Post by cpetercarter on 2008-07-17
/home/[yourusername]/desktop

---

### Post by lupinesoul on 2008-07-17
Thanks.  I just needed it for use in the terminal.

---

### Post by Vivaldi Gloria on 2008-07-17
> **cpetercarter said:**
> /home/[yourusername]/desktop

Linux is case sensitive so it's "Desktop".

On a side note - In international versions it is NOT called Desktop. So it's not a good idea to put a script on the web which uses ~/Desktop.

---

### Post by Joeb454 on 2008-07-17
Well the majority of the forum (excluding the international sub-forums) is in English, so giving ~/Desktop as the easy way to get to the Desktop Dir. from the terminal is logical, in my opinion anyway :)

---

### Post by lupinesoul on 2008-07-17
Umm... It says it can't find it.  I'm trying to open the .bin file for java, which is located on the Desktop.

---

### Post by jonian_g on 2008-07-17
open terminal and type:

```
cd Desktop
```

and you are in the Desktop folder or you can place it in user folder and access it just by opening terminal

To run a .bin file, once you get in the directory that contains it, type

```
sh *.bin
```
or
```
./*.bin
```

---

### Post by Vivaldi Gloria on 2008-07-17
> **Joeb454 said:**
> Well the majority of the forum (excluding the international sub-forums) is in English, so giving ~/Desktop as the easy way to get to the Desktop Dir. from the terminal is logical, in my opinion anyway :)

Sure. I didn't say anything against it. I just said as a sidenote that it's not a good practice to use ~/Desktop in scripts.

---

### Post by Vivaldi Gloria on 2008-07-17
> **lupinesoul said:**
> Umm... It says it can't find it.  I'm trying to open the .bin file for java, which is located on the Desktop.

Desktop is the area you can see. If there is nothing there then it's not in the desktop.

You should use the synaptic program to install programs. It's in the top panel, system menu > admin.

Start synaptic, enable restricted and multiverse repositories from the settings. Then click refresh. Then search & install whatever you want.

I suggest you install ubuntu-restricted-extras which contains java, codecs, and other useful things.

---

### Post by lupinesoul on 2008-07-17
Okay, I'm in the Desktop now.  How do I open it?  Sorry.  As you can tell, I'm a complete noob with Ubuntu.

---

### Post by Vivaldi Gloria on 2008-07-17
> **lupinesoul said:**
> How do I open it? 

What are you trying to do? Install java?

---

### Post by lupinesoul on 2008-07-17
> **Vivaldi Gloria said:**
> What are you trying to do? Install java?

Exactly.

---

### Post by Vivaldi Gloria on 2008-07-17
> **lupinesoul said:**
> Exactly.

Welcome to linux mate. The linux way of installing things is very different. You use synaptic to install programs. It's in the top panel, system menu > admin.

Start synaptic, enable restricted and multiverse repositories from the repository settings. Then click refresh. Then search & install whatever you want in synaptic.  

I suggest you search & install ubuntu-restricted-extras which contains java, codecs, and other useful things.

---

### Post by oldos2er on 2008-07-17
> **lupinesoul said:**
> What is the desktop directory in Ubuntu?

 You should read [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

 And I second the recommendation to install ubuntu-restricted-extras.

---

### Post by Aiolos on 2011-06-21
> **Vivaldi Gloria said:**
> Desktop is the area you can see. If there is nothing there then it's not in the desktop.

You should use the synaptic program to install programs. It's in the top panel, system menu > admin.

Start synaptic, enable restricted and multiverse repositories from the settings. Then click refresh. Then search & install whatever you want.

I suggest you install ubuntu-restricted-extras which contains java, codecs, and other useful things.

You didn't find it because you failed to capitalize "Desktop", like me. I just wasted 15 minutes of life on what was a correct intuitive guess for Desktop directory path-name, but I didn't know this word of all Ubuntu words had to be capitalized. Where else but in this haystack is that needle to be found?

---

