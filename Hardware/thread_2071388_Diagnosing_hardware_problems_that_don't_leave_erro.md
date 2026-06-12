---
title: "Diagnosing hardware problems that don't leave errors."
date: 2012-10-15
forum: Hardware
---

### Post by JordanH on 2012-10-15
Hi All,
Last night I was watching a recorded tv show from an external hdd that is connected to my eSata back port on my Asus P5Q-E motherboard.  The machine is roughly idle as the 8GB of mem and Q9550 running Ubuntu 10.04.4 are barely working when I begin to notice that the show I'm watching begins to pause/freeze/glitch/stutter before carrying on.  As I work through a couple episodes, pause happens more frequently and I hear an audible hdd 'clunk'.  Naturally I begin to trouble shoot the hdd.

mplayer, running from the CLI (as always) shows no errors, no skipping and no indication that it has paused.
mplayer, running the same file from a different HDD does not pause/freeze on this file.

smartctl -a, There are no errors recorded.
dmesg, there are no unusual or recent messages.
syslog, there are no unusual or recent messages.
hdparm -t, Read speeds are showing 100-125MB/s which is higher than I would expect.
iostat, all normal.

I unmount the drive...
fsck, Takes excessively long to run.  The only error is that lost+found directory is not found.
iostat -c 2, Running iostat during fsck shows 15-25%, mostly 20%+ iowait%.

The slow fsck and high iowait times tell me there's something funky happening with that disk or controller... but what?

smartctl -l short, "Compelted without error" and shows 19329 lifetime hours.

badblocks, reading at a rate of near 130MB/s the system continues to show 20-25% iowait% ..... It's still running as I post this.

So at this point, I'm thinking it's not the hard drive but I'm not sure what else it could be.  I don't think it's X or mplayer as the freeze doesn't happen when running from other drives.  I don't know why there'd be a corresponding clunk from the hdd if it wasn't a hardware problem.  Perhaps the Marvell sata controller... but how does one test that?

Any thoughts?  What else would you test?

---

