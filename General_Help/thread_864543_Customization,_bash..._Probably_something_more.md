---
title: "Customization, bash... Probably something more"
date: 2008-07-19
forum: General Help
---

### Post by Melindrea on 2008-07-19
Sorry about the not-too-informative header, I have a few very random questions, and I have a feeling it's better I make a single post with all the questions rather than several; one for each topic.

1. Is there a way (I'm guessing yes) to change the little icon next to applications? I'm starting to want the Gnome foot rather than the ubuntu circle.

2. Trying to learn BASH. I have a background in programming, so with that in mind, any suggestions on good resources? Books or online, where I think I prefer online (as long as it's gathered in one place). I've googled for various things when I've needed them (and picked up some info from that), but I'd like a bit more controlled environment.

3. Using conky, I'm somewhat confused on exactly how to call the different functions - are they in conky, or part of the operating system? If the second, any way I can get a list over various bits I can use (apart from the marvellous "show me your conkyrc" that I started from)?

4. How do I find which processes/connections are running?

5. I'm sure there was something else. Ah well. Thanks for reading through the post, I'm having  more fun tinkering with Ubuntu than I've ever had on Windows (though still going to keep it until the last few programs I need are solved!)

Thank you,
Melindrea

---

### Post by sisco311 on 2008-07-19
4.)
```
ps
```
```
ps aux
```
```
top
```
for more info:
```
man ps
man top
```

---

### Post by sdennie on 2008-07-19
1) You should be able to.  Hit Alt-F2 and type gconf-editor.  Navigate to /apps/panel/objects/menu_bar_screen0.  Select use_custom_icon and then in the custom_icon field, put a path to your custom icon (no file browser here so, you'll need to know the full path).

2) There are many resources on this.  A simple google search turned up this 3 part intro from IBM that looks decent: [http://www.ibm.com/developerworks/library/l-bash.html](http://www.ibm.com/developerworks/library/l-bash.html).  If you don't mind getting a book, the book Unix Power Tools is great if you already for picking up tips and tricks.

4) You could use one of the following:

```

ps aux

```

Or, to see what's running in a monitor:

```

top

```

For connections, something like this might be what you are looking for:

```

sudo netstat -anpt

```

---

### Post by bab1 on 2008-07-19
From the Ubuntu forums: [[COLOR="DarkOrange"]Some practical examples[/COLOR]]("http://ubuntuforums.org/showthread.php?t=616875")

And of course the man pages```
man bash
```

---

