---
title: "Keyboard configuration: how to get the &quot;ç&quot; character?"
date: 2010-04-04
forum: Hardware
---

### Post by galobuntu on 2010-04-04
Dear all, 

I am a new [SIZE=3]**ubuntu**[/SIZE] user and I've been having some issues with the keyboard. My mother tongue is Portuguese (Brazil) and I can't get the C with cedilla character (**ç**) when using ubuntu. Although I bought my current laptop in the United States, it was pretty easy to set the keyboard confuguration to *US-International* on[SIZE=3] Windows Vista[/SIZE] and get all the characters I need in Portuguese (not only the ç, but also á, é, í, ó, ú, â, ê and so on).

When I first installed [SIZE=3]ubuntu[/SIZE], I set my keyboard to *USA Alternative International* (former *usa_intl*) under the** keyboard preferences** (*System>Preferences>Keyboard*), but it's not working the same way the *US-International* configuration works on Windows. For instance, if I want to get the "ç" character in Windows, I just use the keystroke** '+C**, but when I do the same stroke on ubuntu, I get the "**&#263;**" character, which I didn't even know it exists until I tried to get the c with cedilla on ubuntu.

The cedilla issue is the one that bothers me the most, but there are minor issues with the keyboard, like** having to push '+space to get the apostrophe** character instead of just **'+letter** (like when I write *it's*), because if I do '+S it returns me a** &#347;** instead of 's. 

Does anyone know how I can fix these issues? I have been trying to use ubuntu as much as I can because I plan to stop using Windows altogheter in the future, but having to open the character map whenever I'm writing an e-mail or a document (text, spreadsheet or presentation) is just too much time-consuming. I might as well just drop ubuntu altogheter instead. 

By the way, my laptop is a [SIZE=3]Dell Inspiron 1520[/SIZE], in case it's necessary to configure the keyboard properly. I hope someone can help me.

Thanks in advance.

---

### Post by paulocoghi on 2010-04-27
This will solve:

[http://havratips.blogspot.com/2007/06/cedilla-cedilha-problem-to.html](http://havratips.blogspot.com/2007/06/cedilla-cedilha-problem-to.html)

---

### Post by paulocoghi on 2010-04-27
If you are using Ubuntu 10.04:

To fix it, edit as root the file /usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules

```
sudo gedit /usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules
```

Find this line:

```
"cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa"
```

And add ":en" after ":wa", so it looks like this:

```
"cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa:en"
```

To fix it also for non-GTK applications, edit as root the file /usr/share/X11/locale/en_US.UTF-8/Compose

```
sudo gedit /usr/share/X11/locale/en_US.UTF-8/Compose
```

and change all instances of  &#263; with ç, and all instances of &#262; with Ç.

---

### Post by galobuntu on 2010-05-10
^^ 
Hi, Paulo.

First of all, thank you for you effort in helping me fix this. I was able to fix the cedilla problem for the GTK-applications, but I still have problem with the non-GTK applications.

What do you mean by > change all instances of  &#263; with ç, and all instances of &#262; with Ç.      ?

When I run 
sudo gedit /usr/share/X11/locale/en_US.UTF-8/Compose
on terminal I get a new notepad document and I'm not sure what to type in there. Also, by any chance, do you know how to fix the code in order not to get the &#7743;, &#341; and &#347; characters? I always get these characters when I'm typing something in English and do the keystrokes **'+m**, **r** or **s** respectively when I want to get 'm (like in I'm), 'r (i.e. you're) or 's (it's). 

Thanks in advance.

---

### Post by mlongman on 2011-04-20
Paulo,

I made all the chages you suggested, but I still get &#263; or &#262;. Is there something I should do to actually activate the changes? Even though I altered the Compose file, it seems to be a tutorial of how to compose the symbols. Many thanks in advance.

---

### Post by leandromartinez98 on 2011-11-30
Please mark this bug:

[https://bugs.launchpad.net/ubuntu/+bug/898419](https://bugs.launchpad.net/ubuntu/+bug/898419)

---

