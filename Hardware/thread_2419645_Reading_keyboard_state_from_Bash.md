---
title: "Reading keyboard state from Bash"
date: 2019-05-24
forum: Hardware
---

### Post by anders.ostling on 2019-05-24
Edit: Moving post to Development

Hi all

We have a number of thin clients with Igel OS (Linux based) equipped with smart card readers. When we remove the smart card, a script is executed and disconnects the remote desktop session. However, we have use cases that require the session to remain on-screen so that another user can insert their smart card for co-signing. What we want to do is the following; When the user removes the smart card, the session disconnects (as today). But if he holds down the left Control key while removing the card, nothing should happen, ie the supplied script should detect that and exit without disconnecting the session.

So I have managed to write a small C program to test for Control down, and it works fine. The executable is linked with libc6 and X11 libs on Ubuntu, and hopefully the libs are compatible with what Igel OS have. Will test that on Monday.

If that does not work, is there any possibility to read the status of meta keys directly from a shell? Since it is an X session, I guess that /dev/console is of no use. Is it possible to read keyboard state at from a script in user mode?

Best regards

---

### Post by sisco311 on 2019-05-25
New post is at: [https://ubuntuforums.org/showthread.php?t=2419767](https://ubuntuforums.org/showthread.php?t=2419767)

Thread closed!

---

