---
title: "monitoring temp,fanspeeds"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by byen on 2005-05-16
hey,
Im a new Linux convert so please bear with me if my Q? sounds dumb....
Is there anyway I can monitor (or control) my laptop temperature ? I have an AMD processor on a Compaq Presario 2100 laptop and really NEED an application which does that. Ive read somewhere that Ubuntu does indeed come with a built-in application ..does anyone know how to fire it on? or do i need to install a third party application? Please suggest.......(my lap is half-cooked with the heat already.... :-# )
thanks for all the help guys.
byen

---

### Post by wildcard on 2005-05-28
emifreq-applet and gkrellm (both available via synaptic) will allow you to monitor temps.

Gkrellm is more versatile and runs on your desktop 

Emifreq-applet runs in your notification tray, and allows you to manually select the speed of your processor-you pick how fast you want your CPU to run. This should help with temperatures.

Also, it couldn't hurt to go to synaptic, find powernowd, and mark it for reinstallation.

---

### Post by CameronCalver on 2006-04-30
what do i type in trminal to get to both those programs

---

### Post by TitusDalwards on 2006-04-30
[QUOTE=CameronCalver]what do i type in trminal to get to both those programs[/QUOTE]
just you have you write this command:
```
sudo aptitude install gkrellm
```
or
```
sudo apt-get install gkrellm
```

standart interface hasc fan speed and temperature if you want you change from configurtion menu or you can download any plugin(lik gkrellm-weather or mailwatch etc.)

---

### Post by CameronCalver on 2006-04-30
when i have downloadedhow do i get into it

---

### Post by TitusDalwards on 2006-05-01
[QUOTE=CameronCalver]when i have downloadedhow do i get into it[/QUOTE]

for downloading and installing just type ```
sudo aptitude install gkrellm
```

if you are talking about plugins:
jusy extract the zipped file and in console type
```
make install
```
thats all.

**note:**for more instructions readme file can help you.

---

### Post by CameronCalver on 2006-05-21
i downloaded both but on gkrellm i cant see where it displays heat and how do you get into emmifreq

---

