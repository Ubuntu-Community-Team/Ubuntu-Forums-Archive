---
title: "Start-up script help. Run as different user."
date: 2008-08-25
forum: General Help
---

### Post by MoriyaMinakata on 2008-08-25
I am trying to get teamspeak to run as a user named teamspeak that I created.

Right now, it starts but it is running as root, which I definately do not want it to do.

Here what the entry in the start up script looks like:

rm -rf /servers/teamspeak/tsserver2.pid
su -u teamspeak
"/servers/teamspeak/server_linux" &

I am not sure if this is the correct syntax.
It was copied from a friend that uses slackware.

Any help would be appricated.
Thanks in advance.

---

### Post by Paindistributor on 2008-08-25
Your script doesn't work the way you want. Let's have a look:

```
su -u teamspeak
```

This command opens a subshell with the teamspeak user.

```
"/servers/teamspeak/server_linux" &
```

But this line doesn't run in your subshell - it runs in the default root environment. That's the problem. :roll:

You should add the -c command instead.

```

rm -rf /servers/teamspeak/tsserver2.pid
su -l teamspeak -c "/servers/teamspeak/server_linux" &

```

That should help your teamspeak work :D

Update: Yes, the syntax was wrong.

---

### Post by MoriyaMinakata on 2008-08-25
When I use that command, I get "su: must be run in a terminal"

---

### Post by caljohnsmith on 2008-08-26
I think you are using the syntax incorrectly with su. Take a look at this thread, as I think it will answer your question:
[http://ubuntuforums.org/showthread.php?p=5662769](http://ubuntuforums.org/showthread.php?p=5662769)

---

### Post by MoriyaMinakata on 2008-08-26
Thanks for the help.
Although, after searching, I found a guide for this specific issue.
It mainly came down to folder/file ownership.

After that was cleared, I was able to make a script to start it and stop it via start-stop-daemon. It then was simply an issue of having it run a start command as the user at boot.

Again, thanks for the help guys.
I am sure that the su command syntax thing will be useful in the future, when I get more running on here.

---

