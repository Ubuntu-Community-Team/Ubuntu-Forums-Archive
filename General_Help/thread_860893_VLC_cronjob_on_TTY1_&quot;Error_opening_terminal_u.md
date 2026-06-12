---
title: "VLC cronjob on TTY1: &quot;Error opening terminal: unknown&quot;"
date: 2008-07-16
forum: General Help
---

### Post by RobertK81 on 2008-07-16
Hi,

to act as an alarm clock, I have set up a cronjob to open VLC at a specific time in the morning and play my favourite playlist.
I can get it to work within the gui using the command export DISPLAY=:0 && vlc -Z /path_to_playlist

However, I can't get it to run on tty1.
Using vlc -Z -I ncurses /path_to_playlist as well as vlc -Z -I ncurses /path_to_playlist > /dev/tty1 works if invoked on TTY1 itself, but not as a cronjob.

In the mail it says 
> VLC media player 0.8.6e Janus
Error opening terminal: unknown.

So, anyone got an idea how to make a cronjob and have its output on TTY1?

Regards,

Robert

---

### Post by zzzuppermen on 2009-02-10
Kind of late answer, but if it may help out anyone, the solution is ```
to export TERM=linux
``` first. Note that if "linux" is not your terminal type, query it by typing ```
echo $TERM
```

Cheers!

---

### Post by Mets on 2009-10-21
thanks zzzuppermen!

To avoid confusion, what he means is that it should look like this:

```

#!/bin/sh
export TERM=linux (or xterm or whatever 'echo $TERM' returned)

<rest of your script>

```

---

