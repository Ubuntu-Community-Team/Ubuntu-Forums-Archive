---
title: "[SOLVED] Running a program after login"
date: 2008-10-01
forum: General Help
---

### Post by DonovanM11 on 2008-10-01
I wrote a program in C++, and I need it to run every time I log in. After 2 minutes, the program is supposed to run firefox and output text to the screen. I use
```
system("firefox");
```
to start firefox. I tried setting it up under sessions, but it didn't work. Firefox never started. Also, I would prefer it to open a terminal so I can see the text my program is outputting. It works fine if I run it from the terminal, but I want it to work on its own.

---

### Post by spiderbatdad on 2008-10-01
I would look at putting it in .bashrc in your home directory.

---

### Post by caljohnsmith on 2008-10-01
> **DonovanM11 said:**
> I wrote a program in C++, and I need it to run every time I log in. After 2 minutes, the program is supposed to run firefox and output text to the screen. I use
```
system("firefox");
```
to start firefox. I tried setting it up under sessions, but it didn't work. Firefox never started. Also, I would prefer it to open a terminal so I can see the text my program is outputting. It works fine if I run it from the terminal, but I want it to work on its own.
Did you make sure your compiled C++ program was executable? 
```
chmod +x firefox_launcher
```
Also, just for troubleshooting, how about make a super simple C program that just writes "executed successfully" to a file on your desktop. That way you can first make sure your C programs are executing OK when you put them in your Sessions. Once you are sure of that then you can probably easily get your firefox program working.

---

### Post by HyperHacker on 2008-10-01
Applications menu -> Settings Manager -> Autostarted Apps. Each of these commands will run at login.

I'm using Xubuntu though, so maybe it's different in Ubuntu.

As for a terminal, I'd just output to a file instead. If you need to see the output in real time, open a terminal and do ```
tail -f /path/to/file
```

---

### Post by DonovanM11 on 2008-10-01
The program that I am trying to get to run is executable. I tried sticking one of my graphics programs in sessions, and it worked fine. For the .bashrc, how do I use that? I don't know if this could be a problem but my program is multi-threaded and the call to firefox is in a different thread.

---

### Post by DonovanM11 on 2008-10-01
I read about .bashrc and figured you meant for me to set up an alias. I set it up and when I execute it through the alias, none of my text is outputted and firefox is not started. I can see it as a process under system monitor, but it is exactly the same as when I ran the original program through sessions. I am currently running it through the terminal and not through sessions.

---

### Post by DonovanM11 on 2008-10-01
I got it working. I went into sessions, and made my command

```
gnome-terminal --working-directory=/path/to/file -x ./file
```

It opened the terminal up and displayed my text perfectly. Firefox also started up perfectly.

---

### Post by karlr42 on 2008-10-01
Thanks for that, I was wondering how to do something similiar for a script I use to download xkcd- it didn't occur to me to issue a command to open a terminal and run my script. Thanks!

---

