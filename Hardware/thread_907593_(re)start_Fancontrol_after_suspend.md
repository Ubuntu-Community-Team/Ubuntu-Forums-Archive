---
title: "(re)start Fancontrol after suspend"
date: 2008-09-01
forum: Hardware
---

### Post by hinge on 2008-09-01
I've been searching the forrum after somthing that should be simple - no luck.
when comming back from a suspend my fancontrol script isn't fired - I can do 
```
sudo /etc/init.d/fancontrol start
```
manually, but how do I make it start automatically ?

---

### Post by hinge on 2008-09-03
All right, I guess this will be yet another conversation with myself...

Whenever I start and stop my fancontrol I do it with this command:

```
sudo /etc/init.d/fancontrol start
```

So I've found the /etc/default/acpi-support file. In there there is a phrase like this:

```

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="fancontrol"

```

I'v tracked this to 
```
cat /etc/acpi/suspend.d/65-services-stop.sh
#!/bin/sh

# Shut down services known to misbehave
for x in $STOP_SERVICES; do
        invoke-rc.d --quiet $x stop
done

```

which is the script responsable for stopping what ever I put in STOP_SERVICES. And this should start them:

```
cat /etc/acpi/resume.d/69-services.sh
#!/bin/sh

# we need to restart our services after the network is back
for x in $STOP_SERVICES; do
        invoke-rc.d --quiet $x start
done

```

But it does not work :confused:

Is it a sudo problem ?
Am I wrong about the procedure ?

HELP

---

### Post by hinge on 2008-09-03
I just got a bit smarter...

Normally when I suspend I go to the K menu -> logout -> suspend.
This does not work - as describe above.

But if I run sudo sh /etc/acpi/sleep.sh - it all works...

So I guess the question is how do I make the  K menu -> logout -> suspend procedure work with the sleep.sh script ?

---

