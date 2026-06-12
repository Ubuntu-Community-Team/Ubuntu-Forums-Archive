---
title: "[SOLVED] Problem creating launcher for matlab"
date: 2008-08-28
forum: General Help
---

### Post by Despot Despondency on 2008-08-28
Hey, I'm trying to create a launcher for matlab on my desktop but seem to be having problems. I created it with the 'create launcher' option and put 

type - application 

and command pointing to the matlab command, /opt/matlab/bin/matlab, in this case.

Now when I double-click the launcher the main window for matlab appears for about a second and then disappears and nothing else happens. I've run the command from the terminal and get no errors. Any ideas? 

Sorry, I've never actually created a launcher before, so it's probably a really stupid question.

---

### Post by Taxman415a on 2008-08-28
That's why I'm never a fan of these launchers because they don't tell you why they fail. An alternative is if you have matlab in your menus and it launches successfully from there is to navigate to it in your menu and drag that to the desktop. That may not work either, but it's worth a shot. If it's not in your menus you could try adding it, but that's just creating a launcher and will probably be the same problem.

---

### Post by prshah on 2008-08-28
> **Despot Despondency said:**
> Hey, I'm trying to create a launcher for matlab on my desktop but seem to be having problems.
type - application 
command - /opt/matlab/bin/matlab


If launching it from the terminal works for you, choose "Application in Terminal" rather than "Application" for "Type".

---

### Post by leepesjee on 2008-08-28
The launcher *did* find your application and actually launched it. Ergo, it did what it's supposed to do. To me, it seems there's nothing wrong with the launcher (Prshah, I've interpreted "Application in Terminal" allways as actually run in a terminal (such as i.e. octave or mc) which matlab doesn't).

Could it be that matlab wants to write some configuration in a working directory at start-up?

---

### Post by prshah on 2008-08-28
> **leepesjee said:**
>  (Prshah, I've interpreted "Application in Terminal" allways as actually run in a terminal (such as i.e. octave or mc) which matlab doesn't).

Your interpretation is a bit off; and there are other issues related to this; best illustrated with an example: I play a lot of slash-em (nethack based game), and if I launch it from the main menu or usig Alt+F2, it does not take into account my custom preferences from the file ".slashemrc" inspite of having successfully exported the SLASHEMOPTIONS (or whatever) environment variable. Slash'Em is definitely not a terminal based game. (OK OK it was, and can be played in the terminal, but I'm talking about Slash'Em-gtk)

Besides, does it hurt to try?

---

### Post by leepesjee on 2008-08-28
Eh no, it sure doesn't, on the contrary.

So it appears it has to do with environment variables. I had not realized that before, but i've experimented a bit now and have seen that variables set in a users .bashrc are not set when you start from a launcher. That could be an explanation of Despots problem.

Do I understand from your story, Prshah, that there are also differences in the variables set when launched as Application vs Application in terminal?

---

### Post by Despot Despondency on 2008-08-29
Cools, thanks for your thoughts. Has it as 'application in terminal' before, but I found it a bit annoying.

Managed to find a suitable thread, [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=754457]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=754457"), which explains the problem. Put -desktop at the end of the command and it seems to be working fine.

---

