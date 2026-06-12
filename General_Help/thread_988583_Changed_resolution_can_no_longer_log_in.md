---
title: "Changed resolution can no longer log in"
date: 2008-11-20
forum: General Help
---

### Post by clancymf on 2008-11-20
I was playing around with the change resolution option and when I restarted my monitor no longer displays ubuntu.  I can get the log in screen but its goes black after that.  ctl alt backspace gets me to the command line.

I have reconfigured xorg.conf to default but the minute i enable my nvidia drivers it goes back to that pre-selected resolution and then BOOM.. blank screen until i kill X.

Any ideas how to change it back so i can use my drivers?

Thanks!!

---

### Post by Marcus Derekus on 2008-11-20
Try completely removing your graphics drivers (so it will remove configuration files) then reinstalling them. Maybe the resolution was set as default on your graphics drivers. so renstalling might set them back to default.

---

### Post by aeronotix on 2008-11-20
I think there's a way to write into the xorg.config file a sort of over-ride resolution that keeps anything else from changing it. If you search for xorg.config editing you might be able to find such a thing, if it exists.

This'll bump it so a guru might find this.

---

### Post by Peter09 on 2008-11-20
If you are running Intrepid- boot into recovery mode and select the xfix option.

---

### Post by aeronotix on 2008-11-20
> **Peter09 said:**
> If you are running Intrepid- boot into recovery mode and select the xfix option.

I think he's done that.

> **clancymf said:**
> 
I have reconfigured xorg.conf to default.

I think the second guy has it nailed.

---

### Post by Peter09 on 2008-11-21
If there is still a problem try installing the nvidia-settings application and running it in a terminal.

```
sudo apt-get install nvidia-settings
```

---

### Post by clancymf on 2008-11-21
Thanks for all the tips.  I'll try them tonight and report back.

---

