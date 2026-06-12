---
title: "kacpid consumes CPU and memory until system dies because of button/lid event"
date: 2009-06-17
forum: Hardware
---

### Post by Kimos on 2009-06-17
I have a brand new Acer Aspire One D150 that I've loaded with a clean install of 9.04 Netbook Remix. Everything except this problem works perfectly out of the box.

When I close the lid, this event is triggered a couple dozen times a second (from acpi_listen):

```

button/lid LID0 00000080 000015a7
button/lid LID0 00000080 000015a8
button/lid LID0 00000080 000015a9
button/lid LID0 00000080 000015aa
button/lid LID0 00000080 000015ab
button/lid LID0 00000080 000015ac
button/lid LID0 00000080 000015ad
button/lid LID0 00000080 000015ae
button/lid LID0 00000080 000015af
button/lid LID0 00000080 000015b0

```

I went in and removed /etc/acpi/lid.sh and commented out the lines in /etc/acpi/events/lidbtn to no avail. I edited lid.sh to just call /etc/acpi/sleep.sh sleep but then when the lid opens it would immediately go to sleep again because of the repeated event.

If I set the event to no action as above, kacpid and kacpid_notify will consume memory and CPU until the system locks up terribly. I was also receiving Xorg oom-killer events as the memory was consumed and the system started killing off processes.

I've been chasing this for more than a week. The OS is perfect, but this problem makes it useless. Disabling ACPI will cost me fan control, battery management, sleep/hibernate, etc. which is not possible on a laptop. 

I am running NBR with this kernel. I can easily provide more information as required

```

Linux pat-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

```

Below is a sample of some of the related bugs I have found. None of them solve this problem, though people seem to receive and solve it randomly.

[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/286604](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/286604)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364592](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364592)
[https://bugs.launchpad.net/ubuntu/+bug/192788](https://bugs.launchpad.net/ubuntu/+bug/192788)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280088](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280088)

---

### Post by Kimos on 2009-06-17
Bug reported here:
[https://bugs.launchpad.net/ubuntu/+bug/388724](https://bugs.launchpad.net/ubuntu/+bug/388724)

The lid events seem to quiet down after the lid has been open for a while. My guess is that it's processing a backlog of events sent by the hardware. I'm going to leave it open and running for a couple days and see if that works. Since manually suspending works I may have a workaround. Just as long as I don't close the lid without shutting down or suspending first I should be alright.

---

### Post by sdennie on 2009-06-17
You could try to blacklist the button module.  I haven't tried that but, it should prevent ACPI button events from being generated.  Adding something like this to /etc/modprobe.d/blacklist.conf should work:

```

blacklist button

```

---

