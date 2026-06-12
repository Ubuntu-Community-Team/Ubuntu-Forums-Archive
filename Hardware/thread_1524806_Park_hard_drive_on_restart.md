---
title: "Park hard drive on restart"
date: 2010-07-05
forum: Hardware
---

### Post by RiggsUSA on 2010-07-05
I have a Acer 8930G, with two sata hdd's Running Ubuntu 10.04
when i first installed ubuntu a year or two ago i noticed my hdd was not parking upon restart and shutdown it sounded like the power was being cut so i looked around the net and fount some commands to enter to park the hdd's shutdown so i made a script (See Below) that i run every time i install any Linux, now the script works great but it is only good for shutdown not restart now some years later can any one help me find out how to have it work for restarting to, so i can  restart my laptop for the first I'm since I've had Linux,

PS. I am no Linux guru i have been using linux for a round two years, and are still learning.

#!/bin/sh

echo "This script needs to be run as root"
echo "Now creating a patch to park your hard drives at shutdown"
sudo touch /etc/rc6.d/S00hdd-shutdown-workaround
sudo echo "#!/bin/sh" >> /etc/rc0.d/S00hdd-shutdown-workaround
sudo echo "echo 1 >> /sys/class/scsi_device/0\:0\:0\:0/stop_on_shutdown" >> /etc/rc0.d/S00hdd-shutdown-workaround
sudo echo "echo 1 >> /sys/class/scsi_device/1\:0\:0\:0/stop_on_shutdown" >> /etc/rc0.d/S00hdd-shutdown-workaround
echo "Patch is now complete you may now shutdown saftly"

---

