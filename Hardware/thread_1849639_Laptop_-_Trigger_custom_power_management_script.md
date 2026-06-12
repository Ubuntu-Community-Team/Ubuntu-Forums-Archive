---
title: "Laptop - Trigger custom power management script"
date: 2011-09-24
forum: Hardware
---

### Post by bblondin on 2011-09-24
Laptop - Trigger custom power management script

I wish to trigger a custom script to run when the AC power is unplugged and then when its plugged in again.

I assume there is a folder were I can place my script.

Does anyone know how I can do this?

Thanks

---

### Post by tgalati4 on 2011-09-24
cat /etc/laptop-mode/laptop-mode.conf

---

### Post by bblondin on 2011-09-27
Thank you for your reply.
I found what I was looking for...

in /usr/lib/pm-utils/power.d/laptop-mode

laptop_mode_ac() {
    # disable laptop mode, set vm parameters back to sane defaults
    if state_exists laptop_mode_default; then
    write_values $(restorestate laptop_mode_default)
    else
    write_values 0 10 5 500
    fi    
---> insert script when on AC /folder/my_script
    echo "Laptop mode disabled."
}

laptop_mode_battery() {
    # enable laptop mode, set vm parameters to buffer as many writes as 
    # possible.
    state_exists laptop_mode_default || \
    read_values | savestate laptop_mode_default
    write_values "$LAPTOP_MODE" "$LAPTOP_DIRTY_RATIO" \
    "$LAPTOP_DIRTY_BG_RATIO" "$LAPTOP_DIRTY_WRITEBACK"
 ---> insert script when on Battery /folder/my_script
    echo "Laptop mode enabled."
}

---

### Post by bblondin on 2011-09-27
[FONT=monospace]Solved[/FONT]

---

### Post by diasf on 2011-09-27
Just for sake of completeness, cpufreqd can also do that. Actually a bit more than that, because each rule can execute commands and you can have multiple rules (like AC power, AC + program XX running, battery more than x% and cpu use less than 10%, etc)

---

