---
title: "Undo action made in terminal"
date: 2008-07-17
forum: General Help
---

### Post by persika on 2008-07-17
Hi, 

By accident I wrote "sudo chmod -R 755 /" in the terminal..
As far as I was able to scroll up the window after I canceled the operation, luckily I couldn't see any permission being changed due to denial of permission to change >permissions<

- HOWEVER, I'm not able to start up a terminal since that mess-up, and I wonder if I can "undo" my chmod and reset all permissions to what they were.

Right now I get the error: "There was an error creating the child process for this terminal."
And when I click OK, there's just an empty terminal with a cursor. No persika@ubuntu $ or what-it's-called.

Im new to linux btw..

---

### Post by phantomjoker on 2008-07-17
755 = The file's owner may read, write, and execute the file. All others may read and execute the file. This setting is common for programs that are used by all users.

You can change the owner of a file by using the ```
chown
``` command.

but you are in very dangerous teritory at the moment. be careful how you proceed.

---

### Post by bodhi.zazen on 2008-07-17
After running that command you are best off reinstalling.

---

### Post by jl884 on 2008-11-24
You can press ctrl+alt+f1 to open up another console, then use chmod commands to restore everything to what it was before.

---

### Post by easoukenka on 2008-11-24
Reinstalling may be best but it goes alphabetically through your directories if that helps.

---

