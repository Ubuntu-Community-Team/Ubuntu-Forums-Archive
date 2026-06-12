---
title: "Fixing increasing Load_Cycle_Count on Ubuntu 11.10 and 12.04"
date: 2012-04-10
forum: Hardware
---

### Post by stchman on 2012-04-10
Hello all, my new Dell Inspiron 15R appears to suffer from increasing load cycle count problem.

After digging around on the Internet, I have formulated a solution.  Thanks to the Linux Mint forum people as well.

The key was to keep the APM_Level at 254 as this will stop the hard drive from spinning down frequently.

Now I know one can do this:
```

sudo hdparm -B 254 /dev/sda

```This is not a permanent solution, to make it permanent you need to edit the hdparm.conf file.

I did as follows:

```

gksudo gedit /etc/hdparm.conf

```Add this line to the very end of the file:

```

/dev/sda {
    apm = 254
    apm_battery = 254
}

```Reboot the laptop and type the following:

```

sudo hdparm -B /dev/sda

```The APM_Level will be 254 for when you are plugged in or on battery.

You can verify that the count is not increasing at an alarming rate by typing the following in a terminal:

```

smartctl -a /dev/sda | grep Load_Cycle_Count

```

Now I know the battery life will be shortened ever so slightly, but I have not noticed any difference.

I am sure someone else has formulated a similar solution and that this might not be unique.

Hope this helps.

---

### Post by aleolivat on 2012-04-12
Excellent.   It is working for me.    I was thinking of downgrading to other version that did not have the problem.

---

### Post by stchman on 2012-04-13
Funny thing is my Acer Aspire One netbook does not suffer from this, but my Toshiba and new Inspiron 15R does.

---

