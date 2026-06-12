---
title: "USB Drive Spindown/Standby in 8.10"
date: 2009-02-17
forum: Hardware
---

### Post by scurra86 on 2009-02-17
Hey,

I have 3 USB harddisks and as I only use them once a day (backups) I would love to have them put to standby automatically. I already know that they are capable of doing so (using g_start --stop /dev/MYDEVICE). I can't really find something like a daemon to automatically do so after a specified period of time (e.g 1 hour). 
I found this (old) posting: [https://help.ubuntu.com/community/ExternalDriveStandby](https://help.ubuntu.com/community/ExternalDriveStandby)
but the script doesn't work as the folder/link hirachy has changed (it seems). I thought it might be possible to fix the script but as I don't understand how idle time is checked and I'm kind of a linux noob I'm a litte bit afraid of messing with the hardware. Can anyone help?

Thanks in advance,
scurra

---

### Post by scurra86 on 2009-02-28
Anyone?:confused:

---

### Post by cprise on 2009-09-20
Sigh.

I wrote that spindown script and was also disappointed when the OS changed and it stopped working. Linux is quite the moving target, especially when your distro (like Ubuntu) upgrades every 6 months. Hence hardly anyone is writing apps for Ubuntu or other Linux-based desktops.

End soapbox.

Anyway the script can no longer daemonize itself because of changes in the OS, so you will need to use a daemon launcher if you want it to start in the background at boot time, like so:

start-stop-daemon -Sbq -x /root/bin/scsi-idle -- 1500

Here is my updated scsi-idle script:
```

#!/bin/bash                     

declare -a DID
declare -a DSTATUS
declare -a DTIME  
declare -a DOFF   


interval=$1
sleepval=40
buspath=/sys/bus/scsi/devices

sleep $sleepval       

while [ true ]; do
thetime=`date +%s`

for scsidev in $buspath/*; do
   if [ -d $scsidev/block ]; then
      devdir=$scsidev/block/*
      devname=`basename $devdir`
      read devsize < ${devdir}/size
      read devremove < ${devdir}/removable

      if [ $devremove -eq 0 ] && [ $devsize -gt 0 ]; then # device is the right type
         read newstat < ${devdir}/stat

         hhit=0; listlen=${#DID[@]}  #; echo $listlen $scsidev

         for ((i=0;i<$listlen;i++)); do
            if [ ${DID[$i]} = $scsidev ]; then
               if [ "${DSTATUS[$i]}" = "$newstat" ]; then
                  if [ $[ ${thetime} - ${DTIME[$i]} ] -ge $interval ] \
                  && [ ${DOFF[$i]} -eq 0 ]; then
                    sg_start --stop /dev/$devname # put into sleep mode
                    # sg_start --pc=5 /dev/$devname # alternate method sleep mode cmd
                    # hdparm -Y /dev/$devname
                     echo stop /dev/$devname
                     DTIME[$i]=$thetime
                     DOFF[$i]=1
                  fi
               else
                  DSTATUS[$i]=$newstat
                  DTIME[$i]=$thetime
                  DOFF[$i]=0
               fi
               hhit=1; break
            fi
         done
         if [ $hhit -eq 0 ]; then   # add new drive to watch list
            DID[$listlen]=$scsidev
            DSTATUS[$listlen]=$newstat
            DTIME[$listlen]=`date +%s`
            DOFF[$listlen]=0
         fi
      fi
   fi
done
sleep $sleepval
done

```

Note the addition of the 'hdparm -Y' method. This is the one I actually use now because sg_start now seems to trigger something in udev that causes the drive to immediately spin back up. The hdparm method now works for my internal SATA drives (where before it didn't). Probably sg_start will work better for external drives like USB and Firewire.

Now, back to my Mac... ;)

---

