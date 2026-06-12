---
title: "texmaker configuration"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by neoflight on 2006-01-08
after a long time of waiting- to get response from someone to help configure kile with texlive installation.... 
i quit kile and now i have texmaker installed. still want to use texlive2005... not tetex.

anyone knows how to configure texmaker? that is to set path and all.. even for a simple one line document i get errors... the first one is " log file not found"...

how do i set path in texmaker? my texlive installation is here....
/usr/local/texlive/2005/bin/i386-linux/ ... if ANYONE using this combination or anyone who knows how to... please reply.... i need to use this to write my papers...

thanks

---

### Post by Susana on 2006-01-08
First I don't use texlive so i don't know if this works, but if all you want is to set the path to the latex related commands go to Options->Configure Texmaker choose one of the commands in there and add all the path to that command. See if it works, if it does write the path to other commands or add the directory to path environment variable.

---

### Post by neoflight on 2006-01-08
thanks...
i gave the path to the latex installation. it doesnt even compile.... the first and only error i get is "log file not found"... i cant find any help on this...i found some page but in hebrew or something...no use...

any ideas?

---

### Post by Susana on 2006-01-09
[QUOTE=neoflight]thanks...
i gave the path to the latex installation. it doesnt even compile.... the first and only error i get is "log file not found"... i cant find any help on this...i found some page but in hebrew or something...no use...

any ideas?[/QUOTE]

If that log is the one that shows in "Messages/Log file" than it should be created when you run latex command. Can you run latex in a terminal? Does it create a file called name_of_your_tex_file.log in the same directory?

---

### Post by neoflight on 2006-02-14
Yes. I could actually see the log file and the dvi etc created when i use latex from the command line or when using gedit. i donno whats happening...

---

### Post by rvm on 2006-07-26
I have installed the windows version of texmaker.  And when I use Quick Build for a valid tex file, I get a message "Log file not found !".  I noticed posts on this forum about this issue.  Is there any solution to it?

---

### Post by mtierney on 2006-12-16
I ran into the same problem with texmaker (no log file found!), but it was because my file was saved as my_file. When I renamed it using "save as" as my_file.tex. Everything compiled correctly and a good pdf was produced. :)

---

