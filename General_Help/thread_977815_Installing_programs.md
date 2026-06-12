---
title: "Installing programs"
date: 2008-11-10
forum: General Help
---

### Post by famico666 on 2008-11-10
Holy F***, I thought Ubuntu was user friendly for normal folk like me. So why am I stuck simply installing the most basic programs?

OK, .deb files are easy, they just install like they're supposed to. But everything else?

Things that have baffled me so far (in various programs):

3. Start Azureus by running the script named 'azureus'; ex. "./azureus" 

*Run*? Where?


1) Edit the Makefile to tell the compiler where to find the X
   and GTK headers and libraries if you do not have the 
   gtk-config script properly installed.  Most systems will not
   need this.


*Edit* How?!


And my favourite, from [http://learn.clemsonlinux.org/wiki/Compiling_programs](http://learn.clemsonlinux.org/wiki/Compiling_programs)

 To run it, usually just do: ./configure 

***Do*** ???? Huh?

Clearly I'm missing something fundamental about Linux, but there don't appear to be any sensible websites that explain how these things work. I take it I need something called synaptic, but even when I tried to download that I got this thing about 'virtual packages' [http://packages.ubuntu.com/dapper/libapt-inst-libc6.3-6-1.1](http://packages.ubuntu.com/dapper/libapt-inst-libc6.3-6-1.1)

So... what am I missing?

At this rate, I'll be going back to Windows.

Your help will be much appreciated. You guys were great helping me get the darned thing installed, looking forward to some help in actually using it.

(Surely I'm not the only person asking these questions... where do you put the people who have similar issues. Is there a dungeon of Linux failures?:confused:)

Thanks guys.

---

### Post by Ryadt on 2008-11-10
To install azureus (now vuze).
Just do ```
sudo apt-get install vuze
```

What version of ubuntu are you using?

---

### Post by igknighted on 2008-11-10
Why are you trying to compile programs from source?  Almost everything is in the standard repo's, and if you need anything else look at getdeb.net or look to add a third party repo called a PPA (personal package archive).  I wouldn't worry about compiling... its an option for advanced users, but 99.9% of people will never do it and really there is no reason to if you don't want to.

---

### Post by Zill on 2008-11-10
famico666:  These links should help...
[URL="http://www.psychocats.net/ubuntu/installingsoftware"]
http://www.psychocats.net/ubuntu/installingsoftware[/URL]
[URL="https://help.ubuntu.com/community/SynapticHowto"]
https://help.ubuntu.com/community/SynapticHowto[/URL]

---

### Post by famico666 on 2008-11-10
Zill, thanks for those links... I'll check them out.

Ryadt, I'm using 8.10.  As I said in my post, I don't have any idea what 'do' means. Do you just have to think really hard? Does closing your eyes help? Squinting? Making a constipated noise?:)

igknighted - I'm not trying to compile, it was just the first thing that made sense from this search: [http://learn.clemsonlinux.org/wiki/Special:Search?search=installing+programs&go=Go](http://learn.clemsonlinux.org/wiki/Special:Search?search=installing+programs&go=Go)

Most programs I've downloaded so far have made no sense to me, so I was fumbling in the dark. Thought 'compiling' was what you did in the world of Linux.

Sorry, no idea what you mean by: "Almost everything is in the standard repo's, and if you need anything else look at getdeb.net or look to add a third party repo called a PPA (personal package archive)"

Right, I'll check out Zill's pages and see if it all makes sense to me in the next five minutes... brb...:p

---

### Post by igknighted on 2008-11-10
Read this guide for installing software (written by one of the moderators here).

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by famico666 on 2008-11-10
Wow guys, Add/Remove, eh? Simple as that. I had expected that was just to remove crappy files that Apple installs when all you want is poxy iTunes.

I feel so much more comfortable now... I have one or two more questions, but to keep this thread on topic I'll post them elsewhere.

---

### Post by spibou on 2008-11-10
> **famico666 said:**
>  
3. Start Azureus by running the script named 'azureus'; ex. "./azureus" 

*Run*? Where?
From the command line. You need to open a terminal emulator first. On Gnome you go to Applications -> Accessories -> Terminal. When at the terminal you go to the directory where you have compiled azureus (or whatever) and you type **./azureus** or possibly **./azureus &** With the second version you can still type commands while the programme is running.

> 1) Edit the Makefile to tell the compiler where to find the X
   and GTK headers and libraries if you do not have the 
   gtk-config script properly installed.  Most systems will not
   need this.


*Edit* How?!
Using a text editor, for example on the command line (terminal) you type **nano filename** where "filename" should be replaced by the name of the file you want to edit. This as general information, editing the gtk-config script is probably too advanced at your present level.

> And my favourite, from [http://learn.clemsonlinux.org/wiki/Compiling_programs](http://learn.clemsonlinux.org/wiki/Compiling_programs)

 To run it, usually just do: ./configure 

***Do*** ???? Huh?
You open a terminal as explained above, you go to the directory where you have expanded the tarball and you type **./configure** You can also do **./configure --help** for a list of helpful options although these will probably confuse you at your present level.

As a general advice, some familiarity with the Linux command line will make your life much easier in the long run.

---

