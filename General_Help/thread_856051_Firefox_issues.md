---
title: "Firefox issues"
date: 2008-07-11
forum: General Help
---

### Post by ptnewby on 2008-07-11
Hello, all....

I've been having the same problem for a while now with firefox. Every now and again, or sometimes everytime fixfox will just exit for no reason. Not savin gmy tabs or webpages i was viewing last. i have ubuntu 8.4 on both my desktop and laptop and the problem only happens on my desktop.

Any help would be great

---

### Post by iaculallad on 2008-07-11
Try renaming your .mozilla directory in your home to something else to reset your firefox setup. A new one will be generated when you start firefox, though you will lose your bookmarks and other personalised settings.

Try to rename/move your .mozilla directory located in your home folder to reset Firefox's settings.

```
mv ~/.mozilla ~/.mozilla.backup
```

Then, restart your Firefox application.

Just in case this does not work, you could always bring back your original .mozilla folder.

```
rm -rf ~/.mozilla
mv ~/.mozilla.backup ~/.mozilla
```

---

### Post by vulcan707 on 2008-07-12
mmm ... seems I am having the same sorts of problem. Upon entering certain web pages like the BBC's ([www.bbc.co.uk](www.bbc.co.uk)), firefox exits completely with no previous warning or error message. I've had Fiferox 3.0 since it launched but this problem started just yesterday.

---

### Post by aysiu on 2008-07-12
Launch the command ```
firefox &
``` from [the terminal](http://www.psychocats.net/ubuntu/terminal). When Firefox randomly closes, you should see an error message in the terminal. Paste that back here.

---

### Post by vulcan707 on 2008-07-12
> **aysiu said:**
> Launch the command ```
firefox &
``` from [the terminal](http://www.psychocats.net/ubuntu/terminal). When Firefox randomly closes, you should see an error message in the terminal. Paste that back here.

I seem to have tracked down the problem to the following plugin that was installed yesterday: Shockwave Flash 10.0.0d525

When I disable it in Firefox the web pages I had problems with will load. But when enabled this is the error message I get in the terminal:

** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805f138: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805f138: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805f138: NP_GetValue
GCJ PLUGIN: thread 0x805f138: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805f138: NP_GetValue return
GCJ PLUGIN: thread 0x805f138: NP_GetValue
GCJ PLUGIN: thread 0x805f138: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805f138: NP_GetValue return

---

