---
title: "hdparm question"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by j-a-p on 2005-12-30
People...

I have a second 60 GB Hard Disk which I use only for backups.  Most of the time it's just spinning for no reason and it's noisy.  So, I use the following command:
```
sudo hdparm -y /dev/hdb
```
to spin it down and shut it up.

My problem is how to automate this at start up, so I don't have to keep on issuing the command and entering a password each time.

Ideally I'd like the drive disabled all the time until I explicitly want to enable it.  How can I accomplish this?

Please help.

Cheers.

---

### Post by John.Michael.Kane on 2005-12-30
I too am looking for how to use hdparm to run comands at startup.

---

### Post by buellman on 2005-12-30
Hi!

Open /etc/hdparm.conf and enter something like this at the end of the file (maybe there where you enable dma like me):
```

/dev/hdx {
        dma = on
        spindown_time = 60
}

```

or if you like cmd in your hdparm.conf

```

hdparm -S 60 /dev/hdx

```

where x is your harddrive. Spindown_time = 60 means the drive will spindown after 5 minutes.

Greets. Buellman

---

### Post by j-a-p on 2005-12-31
This did it for me:
```
command_line { hdparm -y /dev/hdb }
```

Thanks for the info.

---

