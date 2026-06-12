---
title: "firefox going bleh"
date: 2008-08-05
forum: General Help
---

### Post by Reinbag on 2008-08-05
Okay, so this is really weird. Recently, my firefox browser has been not working. Well, I mean it displays pages fine and can download, but the buttons on the top of the browser don´t work. I can´t go back or forward pages, and it doesn´t save my homepage (even w/ commands instead). 

This happened before and I unistalled it, updated, and reinstalled and it worked fine for like an hour. Than, I tried saving a webpage. I downloaded it to my desktop, but it didn´t appear on my desktop. When I tried to move it to a different directory Ubuntu wouldn´t let me. Nautilus gave me an error telling me it couldn´t open my ¨Computer.¨ Then, the firefox window closed (when I wasn´t paying attention) and when I reopened the browser I don´t have buttons anymore. I´ve since tried reinstalling, but that does not work anymore. I have firefox 3.0 and am running Hardy. This is really annoying, but I doubt it´s anything too serious.

---

### Post by anotherdisciple on 2008-08-05
Have you tried deleting your firefox profile? Just go to your home folder and hit Ctrl+H to show the hidden files... and delete the ".firefox" folder. then open firefox back up. It will make you lose all of your bookmarks and stuff... if you want to do this and back up your old profile type this in the terminal:

```
mv ~/.firefox ~/.firefoxbackup
```

---

