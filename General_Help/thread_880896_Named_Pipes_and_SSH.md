---
title: "Named Pipes and SSH?"
date: 2008-08-05
forum: General Help
---

### Post by lyric0n on 2008-08-05
Hi,

I would like to be able to connect to a server via SSH automatically, start a few operations, put SSH into the background (and not see what that SSH is outputting to the screen), load another SSH session, and repeat the process. Then after some given amount of time, go through the SSH sessions, send a few commands, and close them out. 

My thought was to do this using named pipes, with a semi-close example shown here: [http://db.ilug-bom.org.in/Documentation/abs-guide/contributed-scripts.html#FIFO](http://db.ilug-bom.org.in/Documentation/abs-guide/contributed-scripts.html#FIFO)

But I am not sure how to get it to be interactive like this. Does anyone have any suggestions?

Chris

---

### Post by Paradoxalley on 2008-08-05
look at "screen" it is a great application that will let you effectively disconnect from a terminal session and reconnect later to check status. I use it all the time to run apps on remote systems without having to maintain an ssh session.

---

### Post by lyric0n on 2008-08-05
Oh, nifty. I like. Thanks!

[http://www.linuxforums.org/applications/the_screen_program.html](http://www.linuxforums.org/applications/the_screen_program.html)

---

