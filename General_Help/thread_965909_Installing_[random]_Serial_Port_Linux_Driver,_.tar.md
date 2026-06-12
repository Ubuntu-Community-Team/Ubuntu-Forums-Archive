---
title: "Installing [random] Serial Port Linux Driver, .tar.gz file"
date: 2008-10-31
forum: General Help
---

### Post by astroryan7 on 2008-10-31
I can imagine there being a lot of threads on this subject, but I've yet to find an adequate solution.  Anyway, I'm trying to communicate with a serial port on a random motor controller (see Superlogics, Model 8033, specifically).  And I need to install the Linux driver for this motor, which can be downloaded from their site in .tar.gz format.  However, I'm unsure how to approach installing this driver.

I do have build-essential installed, as I've read that is necessary.  I then extract the .tar.gz and go to that extracted directory.  But then, it seems the next most frequent suggestion is to type:

```
./configure
```

which I think is only possible if the driver comes with that script (I have no clue how to verify that).  But it doesn't matter because I get a "no such file or directory" response.  I've then seen suggestions of typing "make" and "sudo make install", but I'm not sure what to do; when I run "make", a ton of error show up.

Any suggestions are most welcomed.  And if anyone feels the urge to try and install the driver themselves, it's found here under "8000 Series Modules Linux Driver":

[HTML]http://www.superlogics.com/downloads.asp?prod=791[/HTML]

Much thanks!

---

### Post by oldos2er on 2008-10-31
I'd start by reading the README.

---

