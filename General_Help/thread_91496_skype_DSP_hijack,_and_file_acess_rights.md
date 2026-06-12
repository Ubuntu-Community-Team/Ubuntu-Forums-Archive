---
title: "skype DSP hijack, and file acess rights"
date: 2005-11-17
forum: General Help
---

### Post by ivanhelguera on 2005-11-17
Hello everyone, 
This sounds like an easy one...
I had a problem with Skype known as 'sound deivce problem' ([http://juljas.net/linux/skype/#hijacker]("http://juljas.net/linux/skype/#hijacker")
I compiled and installed the skype dsp hijacker 
[http://195.38.3.142:6502/skype/]("http://195.38.3.142:6502/skype/")
```

marcinek@ubuntu:~/skype_dsp_hijacker-0.6$ sudo su
root@ubuntu:/home/marcinek/skype_dsp_hijacker-0.6# make && make install
gcc -O2 -Wall -ldl -shared -fpic skype_dsp_hijacker.c -o libskype_dsp_hijacker.so
cp libskype_dsp_hijacker.so /usr/local/lib
cp skype_dsp_hijacker /usr/local/bin

```
I was then able to run the app, but only as a root. ```
marcinek@ubuntu:~/skype_dsp_hijacker-0.6$  skype_dsp_hijacker /bin/bash: /usr/local/bin/skype_dsp_hijacker: Permission denied
```
So i chmoded it so it be executable by everyone 
```
 sudo chmod o+x /usr/local/bin/skype_dsp_hijacker
marcinek@ubuntu:~/skype_dsp_hijacker-0.6$ ls -l /usr/local/bin/skype_dsp_hijacker
-rwx-----x  1 root root 2320 2005-11-17 11:02 /usr/local/bin/skype_dsp_hijacker
marcinek@ubuntu:~/skype_dsp_hijacker-0.6$  skype_dsp_hijacker /bin/bash: /usr/local/bin/skype_dsp_hijacker: Permission denied
marcinek@ubuntu:~/skype_dsp_hijacker-0.6$ sudo chmod g+x /usr/local/bin/skype_dsp_hijacker
marcinek@ubuntu:~/skype_dsp_hijacker-0.6$  skype_dsp_hijacker /bin/bash: /usr/local/bin/skype_dsp_hijacker: Permission denied
marcinek@ubuntu:~/skype_dsp_hijacker-0.6$ ls -l /usr/local/bin/skype_dsp_hijacker
-rwx--x--x  1 root root 2320 2005-11-17 11:02 /usr/local/bin/skype_dsp_hijacker
marcinek@ubuntu:~/skype_dsp_hijacker-0.6$

```
But I still can run it only as a root!
```
marcinek@ubuntu:~/skype_dsp_hijacker-0.6$  skype_dsp_hijacker /bin/bash: /usr/local/bin/skype_dsp_hijacker: Permission denied
marcinek@ubuntu:~/skype_dsp_hijacker-0.6$ sudo skype_dsp_hijacker
Password:
hijacker: skype_dsp_hijacker v0.6
hijacker: when Skype opens DSP /dev/dsp
hijacker: - microphone used: /dev/dsp
hijacker: - speakers used:   /dev/dsp
hijacker: when Skype opens mixer /dev/mixer
hijacker: - mixer used: /dev/mixer

```
What's on?
Best, 
IH

---

### Post by ivanhelguera on 2005-11-17
OK, it was so easy that I solved it myself... I just needed to set the read rights as well. 
Best IH

---

