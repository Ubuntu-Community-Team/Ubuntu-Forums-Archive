---
title: "Trouble with wake on usb and systemd"
date: 2015-05-24
forum: Hardware
---

### Post by Eduardo_Rivera on 2015-05-24
Hello, I'm having troubles getting my install to suspend.

The problem seems to be a couple of wakeup ports, specifically the ports 'XHC' 'EHC1' and 'EHC2'

Whenever I change the setting with "echo XHC > /proc/acpi/wakeup" changes made are not persistent.

So I fixed it by creating the following suspend Hook
```
#!/bin/bash
case $1 in
    hibernate)
            echo "Going to suspend to disk!"
            ;;
    suspend)
            echo "Fixing acpi settings."
            for usb in 'XHC' 'EHC1' 'EHC2';
            do
                    state=`cat /proc/acpi/wakeup | grep $usb | cut -f3 | cut -d' ' -f1 | tr -d '*'`
                    echo "device = $usb, state = $state"
                    if [ "$state" == "enabled" ]
                    then
                            echo $usb > /proc/acpi/wakeup
                    fi
            done
            echo "Suspending to RAM."
            ;;
    thaw)
            echo "Suspend to disk is now over!"
            ;;
    resume)
            echo "We are now resuming."
            ;;
    *)
            echo "Somebody is callin me totally wrong."
            ;;
esac

```
However with the new systemd this solution isnt working anymore, I  managed to create and place the same script on  /usr/lib/systemd/system-sleep/, however this doesnt work as it doesnt  execute, here is the output of my journal

[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"][/TD]
[/TR]
[/TABLE]

```
may 22 22:59:43 waiobook systemd[1]: Starting Suspend...
may 22 22:59:43 waiobook systemd-sleep[1372]: Suspending system...
may 22 22:59:49 waiobook systemd-sleep[1372]: System resumed.
may 22 22:59:49 waiobook systemd[1]: Started Suspend.
may 22 20:09:03 waiobook systemd[1]: Starting Suspend...
may 22 20:09:03 waiobook systemd-sleep[2674]: Suspending system...
may 22 20:09:07 waiobook systemd-sleep[2674]: System resumed.
may 22 20:09:07 waiobook systemd[1]: Started Suspend.
```

I guess maybe the hook is formated wrongly, but i lack the knowledge to fix it, as i'm not sure what changed between upstart and systemd.

Any help is greatly apreciated.

Cheers.

---

### Post by dino99 on 2015-05-25
you should report against systemd

---

### Post by thornton-ma on 2015-07-01
The script parameters have changed as well.  $1 is "post" on resume, "pre" otherwise. $2 in both cases contains either "suspend", "hibernate", or "hybrid-sleep".  Modifying your example:

```

#!/bin/bash
case $1 in
    pre) case $2 in
        hibernate)
                echo "Going to suspend to disk!"
                ;;
        suspend)
                echo "Fixing acpi settings."
                for usb in 'XHC' 'EHC1' 'EHC2';
                do
                        state=`cat /proc/acpi/wakeup | grep $usb | cut -f3 | cut -d' ' -f1 | tr -d '*'`
                        echo "device = $usb, state = $state"
                        if [ "$state" == "enabled" ]
                        then
                                echo $usb > /proc/acpi/wakeup
                        fi
                done
                echo "Suspending to RAM."
                ;;
        *)
                echo "Somebody is callin me totally wrong."
                ;;
        esac ;;

    post)
            echo "We are now resuming from $2."
            ;;
    *)
            echo "Somebody is callin me totally wrong."
            ;;
    esac


```

---

