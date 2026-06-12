---
title: "Laptop Lid State Always Closed"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by Elitist_Phoenix on 2008-02-11
Basically my laptop lid is always detected as closed even though its open. Now the problems is that this cause X to say there are no usable screen modes present.

I'm using hardy heron alpha 4

Disabling acpi (acpi=off) at boot by passing arguements to the kernel, fixes this problem and it works fine.

With acpi on:
root@discostu:/home/discostu# cat /proc/acpi/button/lid/LID/state
state:      closed

This approach fails:
```

( UDI=`hal-find-by-property --key info.product --string 'Lid Switch'`
echo $UDI
echo DELAYING force lid open...
sleep 5
hal-set-property --udi $UDI --key button.state.value --bool false
echo FORCED lid open = $?
)& 

```


WHAT I'M ASKING IS... How do i force the proc filesystems state to "open"?
Also should i file a bug report for this?


Extra Info

root@discostu:/home/discostu# lshw
discostu                  
    description: Notebook
    product: Satellite A70
    vendor: TOSHIBA
    version: PSA70A-007001
...
     description: VGA compatible controller
     product: RS300M AGP [Radeon Mobility 9100IGP]

---

### Post by Elitist_Phoenix on 2008-02-11
Can't echo "open" into that file cause i get an I/O error. Has anyone got any suggestions?

---

### Post by Elitist_Phoenix on 2008-02-21
Come on people any suggestions it really annoys me cause i can't use acpi and my laptop battery died today and i got no warning. Will file bug report in 2 days if i haven't got any responses

---

### Post by Elitist_Phoenix on 2008-02-23
w00t w00t! seems to be fixed with and upgrade from around last night sometime.

---

