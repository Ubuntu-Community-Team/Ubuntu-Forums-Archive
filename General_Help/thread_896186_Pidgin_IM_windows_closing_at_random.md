---
title: "Pidgin IM windows closing at random"
date: 2008-08-20
forum: General Help
---

### Post by chorca on 2008-08-20
I've been having an issue with Pidgin for awhile now. The latest releases haven't fixed it, and it's been happening on two separate installs of Hardy.

Basically, I'll have an IM window open with someone. They'll start typing, and it will show that. As soon as they send the message, before it even displays it, their window or tab will close. No error message, no nothing.

This seems to be some sort of crash, because the option to not close windows immediately when clicking the close button would usually show the previous conversation if that buddy's window was opened again, however, when I reopen the window, the message list is blank.

I've tried disabling all plugins I had enabled with no help. It does not occur constantly, just two or three times max per session (though i'm only on for a few hours at a time).

I've tried starting Pidgin from the command line, but no errors are dumped. I've run it with the Debug Window open, but when the problem occurs, there's nothing written to it. It only happens when I receive a message from someone.

While this isn't an enormous issue, it's definitely very annoying to have to ask the other person to repeat themselves because my client keeps closing the window.

I've searched on both LaunchPad, as well as Pidgin's bug reports and the forum here and not found anything relating to this, so I"m wondering if i'm the only one having this issue. The fact that it happens across multiple computers though makes me think it might be bigger than one messed up install or something.

Any help with this is appreciated.

---

### Post by tuxxy on 2008-08-20
You attempted a reinstall?

---

### Post by chorca on 2008-08-20
I have not done a total reinstall yet, but the issue is happening on two separate computers. If it's what has to be done, I'll do it one one of them and see what happens.

A complete reinstall seems a bit much for such a small problem. One reason I've been holding off on doing that is I've got everything configured the way I like it and it's a decently-sized hassle to redo.

---

### Post by Tiftof on 2008-08-21
I'm having the same problem... Haven't found a solution yet, nor have I have I found what exactly makes the chat window close from time to time...

---

### Post by chorca on 2008-08-21
Alright, well It's good to know I'm not the only one. Anybody else? Perhaps we should file a bug report?

---

### Post by forger on 2008-08-21
Have you tried pidgin 2.5?
[http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin)

Note that you have to remove your old versions before installing:
```
sudo apt-get remove pidgin pidgin-data libpurple0
```

---

### Post by chorca on 2008-08-21
Haven't yet, thought 2.4.3 was the latest. I'll give it a shot when I get home.

---

### Post by Mhurst1 on 2008-08-21
You should also try opening pidgin in a terminal window and when it shuts down see what error comes up. I do not have this issue.

---

### Post by chorca on 2008-08-21
Right, I tried that as I stated in the original posts, no errors were given when a window closed. It seemed to be an internal problem, like something unforseen happens and the window closes, but no error messages are output. I was thinking of running the debug version, but I thought those were only for segfault crashes and the like.

---

### Post by Coreigh on 2008-08-21
This happens to me too on Hardy. If I run from command line it returns "Segmentation Fault" when the crash happens (I have not done --debug yet). Additionally I can not get the librvp plugin to work AT ALL, will not connect. Returns an error that says "the server returned an empty response to SUBSCRIPTION request" Pidgin and librvp work perfectly on Gusty with the same Exchange 2000 server.

---

### Post by chorca on 2008-08-21
Well i've been testing 2.5 since I got home, and it just closed a window as I was receiving a message. Person was typing, and suddenly the window closed. Still not sure what's causing this. Any other way to get debug information?

To clarify, Pidgin isn't crashing. Just one tab or IM window is closing. If i have 5 tabs open in a window and this issue occurs, I now have 4 tabs open. If there's only one tab in a window and it happens, that window only closes. Buddy list and everything else is still running, and there's no indication of it happening on the command line or in the debug window.

---

### Post by khc on 2008-08-22
try help->debug. I have no idea why this would happen though. is it just the other person typing, or are you typing too?

---

### Post by chorca on 2008-08-22
When receiving a message. If someone sends you a message, the instant you receive that message, the window/tab will close. There's nothing output to the debug logs, or to the command line, so it's difficult to track down what's causing this.

---

### Post by chorca on 2008-08-23
Well, it's been a few days, i suppose this post has been dropped down in the list..


I've done a bit of research on my own, it appears a bug was filed with Pidgin for this issue 8 months ago. The devs instated a fix, which they thought resolved the issue in 2.4.0, however, people began posting that it did not, so the bug was reopened, and the last post on it was 4 months ago.

2.5.0 is still having the same problem, so I'm thinking that it's definitely not just a handful of people having the problem.

[http://developer.pidgin.im/ticket/4442](http://developer.pidgin.im/ticket/4442) (Link to the bug report)


UPDATE:

According to the trouble tickets, a workaround is to make sure the "Close IMs immediately" option is turned on. Aparrantly the issue stems from this option being turned on. It doesn't appear that there's a fix for it yet, but that's the temporary workaround.

---

