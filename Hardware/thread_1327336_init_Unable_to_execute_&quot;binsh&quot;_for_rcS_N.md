---
title: "init: Unable to execute &quot;/bin/sh&quot; for rcS: Not a directory"
date: 2009-11-15
forum: Hardware
---

### Post by JackAcid on 2009-11-15
Running 8.04 LTS on a Sony VAIO (for over a year now)

I was trying to watch a dvd on my laptop and got an error message telling me it could not mount the drive. I thought a simple re-boot would help. Instead I got the following error message:

init: Unable to execute "/bin/sh" for rcS: Not a directory
init: rcS main process (709) terminated with status 255
init: Unable to execute "bin/sh" for rc-default : Not a directory
init: re-default main process (710) terminated with status 255

and now it will not get past this.

I saw the same problem posted in the server platforms with no replies, thought maybe someone here may have an answer? I thought I would try here before doing a flatten and re-load.

Thanks!
J.A.

---

### Post by nixscripter on 2009-11-18
Startup scripts usally look for /bin/sh to execute themselves. If it thinks that's a directory, it might be caused by some sort of path problem.

You boot into single user mode to look around, and that stuff won't run. The easiest way is to edit the kernel command line:

1. When it says "Booting, press ESC 3...2...1.." hit escape.
2. You will see a menu. Type 'e'
3. Using the arrow keys, select the "kernel" line. Append the word "single" and press enter.
4. When you go back to the list of lines, hit "b"

---

### Post by JackAcid on 2009-11-21
Thanks for the reply! I did not see this until I had re-installed Ubuntu 8.04.
It's good to know there is a way to look at what is going on.

I will keep this bit of knowledge set aside for the next time (5 years hence?)

I had tried to boot the recovery kernels, but kept getting the same message, so I figured that partitions files had been corrupted some way, That and none of the live CD's I have would mount anything except the boot partition. They could see that there was something there, but could not determine which file system.

Thanks again for the info, I really do appreciate it! learning something new is always a win!

Jack

---

### Post by nixscripter on 2009-11-21
Glad to help.

So when you boot in single user mode, what is the first line of the failing scripts? What happens if you run /bin/sh?

---

