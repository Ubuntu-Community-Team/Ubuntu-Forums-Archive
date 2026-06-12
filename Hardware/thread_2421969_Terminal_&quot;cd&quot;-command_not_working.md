---
title: "Terminal: &quot;cd&quot;-command not working"
date: 2019-06-30
forum: Hardware
---

### Post by linuxo2 on 2019-06-30
Hello!
I am a new Linux-User and have trouble installing printer/scanner-drivers as I cannot run "cd"-command on my terminal. I am using Ubuntu 18.04.2 LTS and a Samsung Xpress M2885 FW.
I downloaded the drivers from Samsung’s website([https://samsung-printerdrivers.com/samsung-printer-xpress-m2885fw-drivers-download/](https://samsung-printerdrivers.com/samsung-printer-xpress-m2885fw-drivers-download/);4[SUP]th[/SUP] from above) and saved it on the desktop as“uld.tar.gz”. As far as I understand, I need to open the downloaded file in Terminal. Hence, I entered “cd” and dragged the file into the terminal window, which yielded the following line: 
“cd /home/mycomputer/Desktop/uld.tar.gz”
However, I keep getting the following response: 
“bash: cd: /home/mycomputer/Desktop/uld.tar.gz: Not a directory”
Next, I had a look at UsingTheTerminal on help.ubuntu.com and just tried some of the given cd-commands, such as “cd/”, “cd~” or“cd..”. None of these work on my computer, as I receive responses like “bash: cd/: No such file or directory” or “cd..: command not found”. 
Your help would be highly appreciated.
Thanks and regards,
linuxo

---

### Post by CatKiller on 2019-06-30
The error message is correct: your tar.gz file is *not* a directory. You can't change directory into something that's not a directory.

You can right-click on the file and select "Extract Here" and *then* you'll have a directory you can change into, and do whatever it is that the files inside need you to do.

Alternatively you can do ```
cd ~/Desktop
tar xvzf uld.tar.gz
```

and then cd into your new directory and do whatever it is that the files inside need you to do.

---

### Post by spjackson on 2019-06-30
> **linuxo2 said:**
> 
Next, I had a look at UsingTheTerminal on help.ubuntu.com and just tried some of the given cd-commands, such as “cd/”, “cd~” or“cd..”. None of these work on my computer, as I receive responses like “bash: cd/: No such file or directory” or “cd..: command not found”. 

See above regarding uld.tar.gz. However, for these 3 failed commands, you need a space between cd and its argument, i.e. "cd /", "cd ~", "cd ..".

---

### Post by linuxo2 on 2019-06-30
Thanks a lot for your answers. Installing the .sd-files worked perfectly now. I still have troubles with the printer drivers but I will address these in a different thread as they do no longer relate to cd-command.

---

### Post by linuxo2 on 2019-06-30
I mean .sh-files instead of .sd-files, of course.

---

### Post by TheFu on 2019-06-30
> **linuxo2 said:**
> I mean .sh-files instead of .sd-files, of course.

Being detailed is critical here, if you want good solutions. Unix doesn't use extensions at all, though a few programs might.  .sh usually means a shell script, but it isn't mandatory, like in Windows.  Files without extensions can be shell scripts too.  If I were creating malware for Linux, I'd put the script into a file with any data file extension (.doc, .xls, .txt, .rtf, .pdf, .html ...), then when someone double-clicks, it would run doing my bidding, for example.
 
If you are going to use CLI/Shell/terminal commands, then a little basic knowledge and organized reference would be strongly suggested.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a no-hassle, well-written, book that you can buy at a bookstore or just download the legal, free, PDF from that link.  Unix skills always build on prior skills, so jumping into the middle is very hard while still a beginner.

---

### Post by linuxo2 on 2019-07-01
Thanks a lot for your explanations and for the suggested reading which I have downloaded immediately. As I have no clue about programming I look forward to now making my first, adventurous steps in this area.

---

### Post by TheFu on 2019-07-01
> **linuxo2 said:**
> Thanks a lot for your explanations and for the suggested reading which I have downloaded immediately. As I have no clue about programming I look forward to now making my first, adventurous steps in this area.

This sort of stuff isn't considered "programming."  Hundreds of millions of Unix users have done this same stuff over the decades. Most are NOT programmers, just regular end-users.

If this specific issue is solved, please help the community and mark it as "SOLVED" using the thread tools button near the top. This tells people looking for a solution that you found it - perhaps if they are having a similar issue, look in here.  It tells all the volunteers that you don't need more help, so they don't waste time reading the thread only to find you've solved it.  Big help if you tell everyone "SOLVED."

---

