---
title: "HDD won't spin down"
date: 2010-06-10
forum: Hardware
---

### Post by WA1DH on 2010-06-10
I'm trying to make the hard drive on my server spin down when not in use. I'd like to keep the server running constantly, but I only access the drive a few times a day. Ideally, I'd like to set it to spin down after 20-30 min of inactivity.

If I try using hdparm -S, nothing happens. It never spins down. If I force spindown with hdparm -Y, it immediately spins back up. It seems like something is writing to the drive every few seconds, keeping it from spinning down (perhaps logging?)  Is there any way to make it spin down when not in use?

HDD is a 1TB WD Caviar Green
I'm running Lucid 10.04
I keep it in runlevel N2 (terminal) as it is a file server

Thanks.

---

### Post by khelben1979 on 2010-06-13
Check out the usage examples on the [hdparm wikipedia]("http://en.wikipedia.org/wiki/Hdparm"). From there I can see that you missed specify the time for it: ```
hdparm -S 5 /dev/hda
```

Did it help?

---

### Post by cascade9 on 2010-06-13
If that didnt help, then you will need to go into your BIOS and check your settings.

---

### Post by WA1DH on 2010-06-18
Tried the hdparm command, it didn't do anything. What am I looking for in my bios?

---

### Post by abdusamed on 2010-06-18
I'm in desparte too..i really don't want ubuntu to wreck my notebook... it's running pretty fast for writing up a simple gedit document! Plus..i haven't enable my swap cuz i wanted to keep my hard drive usage as low as possible,,,it doesn't feel like working!

i get this message after runnin command....

```

bahie@bahie-laptop:~$ hdparm -S
  -S: bad/missing standby-interval value (0..255)

```

after after running 
hdparm -S 5 /dev/hda

my hd spins down but spins up in a second

---

### Post by abdusamed on 2010-06-19
what's the problem? is it possible to view the process which is accessing the hard disk for read/write?

---

### Post by npjoseph on 2011-07-19
Here's what I found in the manpage for hdparm. It explains the working of the -S flag with hdparm.

       -S     Put the drive into idle  (low-power)  mode,  and  also  set  the
              standby (spindown) timeout for the drive.  This timeout value is
              used by the drive to determine how long to wait  (with  no  disk
              activity)  before  turning  off the spindle motor to save power.
              Under such circumstances, the drive may take as long as 30  sec&#8208;
              onds  to respond to a subsequent disk access, though most drives
              are much quicker.  The encoding of the timeout value is somewhat
              peculiar.   A  value  of zero means "timeouts are disabled": the
              device will not automatically enter standby mode.  Values from 1
              to  240 specify multiples of 5 seconds, yielding timeouts from 5
              seconds to 20 minutes.  Values from 241 to 251 specify from 1 to
              11 units of 30 minutes, yielding timeouts from 30 minutes to 5.5
              hours.  A value of 252 signifies a  timeout  of  21  minutes.  A
              value  of 253 sets a vendor-defined timeout period between 8 and
              12 hours, and the value 254 is reserved.  255 is interpreted  as
              21  minutes  plus  15  seconds.  Note that some older drives may
              have very different interpretations of these values.

Note that a value of 5 does not translate to an absolute value of 5 minutes. I think you should set your value to 252.

---

