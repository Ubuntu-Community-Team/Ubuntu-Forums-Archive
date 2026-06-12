---
title: "Multiple commands with input from gnome launcher"
date: 2008-08-06
forum: General Help
---

### Post by genericnumber1 on 2008-08-06
I'm trying to do multiple things with one button push of the launcher... Typing in the two commands separated by a semicolon directly into a terminal works fine, but I'm hoping to do something like this by just pushing one button.

I need to first log into ssh (with typing in the pass) and then start a non-daemon app after typing in my ssh pass.

I've tried creating a launcher and putting the commands in directly, separated by a semicolon. I've also tried running the command "gnome-terminal -x <my commands>". The last thing I tried was to create a gnome-terminal profile for the commands and run it with the option to keep the window open... all to no avail.

I searched the forums for similar problems, and tried multiple suggestions, etc, but none worked for my particular problem unfortunately.

---

### Post by caljohnsmith on 2008-08-06
You could do something like:
```
gnome-terminal -x bash -c "cmd1; cmd2; read -n1"

```
That will execute cmd1, then cmd2, and finally it leaves the terminal window open until you hit any key (read -n1), and then the terminal window closes. Is that maybe what you are looking for?

---

### Post by genericnumber1 on 2008-08-06
It worked perfectly, thanks so much.

---

### Post by benjoseph on 2008-09-22
[COLOR="Blue"]Hi to every one. I have my delete bin basket with 400 MB of Mp3 files that there i no way I can delete. I have tried every thing suggested in the forum. I have even installed Fedora 8 with the hope it would have wipe my H.D clean, but with a great dismay when I reinstalled Hardy Heron the damn files where still there. I know that this sound silly, but I get very frustrated by such stupid things. Sound stupid, but having this problem cut short my enjoyment of using Linux to whom I am very delighted. Please because I am an old user (sixty-four) I am not very good with the computer, and I am not sure I will be able to return to this post for your replay. What I need to know really is to know how to format the system and start afresh.Can you be so kind to email me your answer also at [email]gruffoni@toucansurf.com[/email] Thank you very much friends, you are a great help. God bless you all· Giacomo[/COLOR]

---

