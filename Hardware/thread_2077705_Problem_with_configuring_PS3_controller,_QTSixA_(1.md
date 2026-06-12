---
title: "Problem with configuring PS3 controller, QTSixA (12.10)"
date: 2012-10-29
forum: Hardware
---

### Post by cphus on 2012-10-29
Hello,

I'm running Ubuntu 12.10 with 3.5.0-17-generic.

I followed the instructions in [here]("http://www.youtube.com/watch?v=C2yKiMxisM0&feature=relmfu") but when I reach the 'sixad --start' step, I press the PS3 button but the device does not vibrate. 

Perhaps I should also mention that I can clearly see the device in QTSixA with the USB and bluetooth address. Also, under Windows(with MotioninJoy DS3), it works. 

Any help would be appreciated.

---

### Post by pecosdave on 2012-11-26
I figured out a nasty work around.  I figured out with all of the init vs. upstart stuff that the sixad stuff was probably loading before BlueZ and that's a problem.

In /etc/init.d/sixad change:
if (sixad_already_running_check "$1"); then
log_warning_msg "sixad is already running"
else
{
log_daemon_msg "Starting sixad"
$DAEMON --start &>>/var/log/sixad &
log_end_msg 0
}
fi


to:


if (sixad_already_running_check "$1"); then
log_warning_msg "sixad is already running"
else
{
log_daemon_msg "Starting sixad"
**sleep 20; **$DAEMON --start &>>/var/log/sixad &
log_end_msg 0
}
fi

You may need to adjust that counter but that worked on my netbook.  Too long didn't work, don't make it too short or it won't do the trick.  Maybe someone who knows more about upstart than I do can convert the sixad script to upstart instead and make it dependent on BlueZ loading first.

---

