---
title: "Voice in movies too low since upgrade to 14.04"
date: 2014-05-12
forum: Hardware
---

### Post by pwlodarczak on 2014-05-12
Hi there,
Since I upgraded to Trusty Thar the voices in movies is covered by the background music and can hardly be understood. This is only the case when using the 5.1 surround system, head phones are working fine. I have an ASRock Vision PC. any ideas?
Cheers
Peter

---

### Post by Kirboosy on 2014-05-12
Perhaps the reason is Pulseaudio is running in 2 channel mode.

```
gksu gedit /etc/pulse/daemon.conf
```

Look for the following line
```
default-sample-channels = 2
```Try changing the line to the following
```
default-sample-channels = 6
```
In order for the changes to take effect you will have to restart the service.
```
pulseaudio -k
```
I can't remember if pulseaudio is automatically restarted with -k so lets double check it.
```
pulseaudio --check
```
If it isn't running then go ahead and start it back with 
```
pulseaudio -D
```

That should fix the issue with your surround not working properly. (I'm not sure if the headphones will have a new issue or not)

Hope that helps!
~Caboose
P.S. make sure that the default-sample channel line doesn't have ; in the beggining. That comments out a line in the config file.

---

### Post by pwlodarczak on 2015-02-05
I reinstalled Ubuntu and now everything is fine. There is a handy tool to configure PulseAudio:
```

paman

```

---

