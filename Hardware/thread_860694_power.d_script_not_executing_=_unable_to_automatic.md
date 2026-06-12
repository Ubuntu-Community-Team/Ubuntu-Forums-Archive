---
title: "power.d script not executing = unable to automatically throttle ATI GPU"
date: 2008-07-15
forum: Hardware
---

### Post by fictivetoast on 2008-07-15
My Compaq 6910p has had a laughably useless battery life on Ubuntu of late, so I reinstalled Hardy and have been trying to tweak things to decrease power consumption while unplugged.

Enabling laptop_mode and making use of intel's powertop have helped a lot, but I'm having trouble getting ATI to default to its lower voltage setting when I'm unplugged.

I've made a script as suggested [here]("http://ubuntuforums.org/showthread.php?t=729644") and installed it into power.d and sleep.d, instructing the computer to switch the ATI to level 1 instead of the higher voltage default level 2 when unplugged... but when I unplug, running "aticonfig --lsp" still tells me that I'm still in level 2.

So either the script isn't being executed at all (quite possible), or the command is somehow not affecting my ATI card as entered in the script.  Can anybody tell me where I'm going wrong here?  Is it possible that the script just isn't running at all?


>>here's the code for the power saving script:
```
#!/bin/bash
if on_ac_power; then
  # Reset back to normal settings
  echo 0 > /proc/sys/vm/laptop_mode
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  # Manually set ati powerplay to default level
  sudo aticonfig --set-powerstate=2
  # Manually set the iwl3945 driver to no power savings.
  echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level 
else
  # Turn on aggressive power savings
  echo 5 > /proc/sys/vm/laptop_mode
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 10 > /proc/sys/vm/dirty_background_ratio
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  # Manually set ati powerplay to lowvoltage level
  sudo aticonfig --set-powerstate=1
  # Manually set the iwl3945 driver to power savings.
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level 
fi
```

---

### Post by wired98 on 2008-07-30
The answer to your problem is quite easy. The aticonfig command can only be issued by the user that owns the current x-session. You can try this by changing to the root account and typing:

```

root@yourbox:/# aticonfig --set-powerstate 2
No protocol specified
No protocol specified
Error: Unable to open display `:0'.
Warning : Option 'PowerState' is exclusive, other options will be ignored.

```

The error message "Unable to open your display `:0'." tells you that the current user is not allowed to manipulate the xsession.

As your scripts are executed by the acpid daemon, and therefore probably by the root user, the aticonfig command will just generate the above error, however, without you seeing it. Hence, you need to change your script in a way that the current owner of the xsession is identified, and then is used to issue the aticonfig command.

Your script has to be changed like this:
```


#!/bin/bash

# Determine X user, script usually runs as root:
getXuser() {
        user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`
 
        if [ x"$user" = x"" ]; then
                user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`
        fi
        if [ x"$user" != x"" ]; then
                userhome=`getent passwd $user | cut -d: -f6`
                export XAUTHORITY=$userhome/.Xauthority
        else
                export XAUTHORITY=""
        fi
}



if on_ac_power; then
  # Reset back to normal settings
  echo 0 > /proc/sys/vm/laptop_mode
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  # Manually set ati powerplay to default level
  for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser
    if [ x"$XAUTHORITY" != x"" ]; then
        # extract current state
	export DISPLAY=":$displaynum"
        su $user -c "aticonfig --set-powerstate 2 2>/dev/null"
    fi
  done
  # Manually set the iwl3945 driver to no power savings.
  echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level 
else
  # Turn on aggressive power savings
  echo 5 > /proc/sys/vm/laptop_mode
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 10 > /proc/sys/vm/dirty_background_ratio
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  # Manually set ati powerplay to lowvoltage level
  for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser
    if [ x"$XAUTHORITY" != x"" ]; then
        # extract current state
	export DISPLAY=":$displaynum"
        su $user -c "aticonfig --set-powerstate 1 2>/dev/null"
    fi
  done
  # Manually set the iwl3945 driver to power savings.
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level 
fi


```

Further I replaced the aticonfig option "--set-powerstate=x" with "--set-powerstate x" because this is the correct syntax for the command as far as I know. Otherwise this will additionally produce a syntax error and the script will not work.

I hope this solution will work for you.

Cheers,

Marc

---

### Post by fictivetoast on 2008-07-30
That's wonderfully helpful!

Having now thrown the Ibed alpha on my laptop, do you happen to know whether the power saving functions are handled any differently on the coming 8.10?  Or should the same scripting work with 8.10 as 8.04?

---

### Post by wired98 on 2008-08-07
Sorry, there I cannot help you, as I have not tried the 8.10 version of ubuntu. 
Usually all the scripts that handle the ACPI functionality have changed slighly between consecutive versions of ubuntu. But usually it was not hard to figure out how to change my old scripts. Concerning the use of the script functions that finds the current xuser and so on, this should work perfectly on any version of ubuntu.

---

