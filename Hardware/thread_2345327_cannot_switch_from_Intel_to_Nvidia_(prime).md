---
title: "cannot switch from Intel to Nvidia (prime)"
date: 2016-12-03
forum: Hardware
---

### Post by bart.vanaudenhove on 2016-12-03
[COLOR=#111111][FONT=Ubuntu]HP Envy dv7 laptop with hybrid graphics (Nvidia and Intel), Ubuntu 16.04.
Nvidia-367 installed and Additional Drivers tells me it's in use. Active card is Intel.
I can startup nvidia-settings and choose nvidia, it tells me to logout and log back in, but active card remains Intel.
When I do ```
sudo prime-select nvidia
``` and then ```
prime-select query
``` it tells me "nvidia", but the active card actually still is Intel (eg. Blender doesn't list a GPU as available for computing, and [this method]("https://www.maketecheasier.com/graphics-card-information-linux/") tells me Intel too.) Logging out and in again still gives me nvidia.

I don't get error messages or other problems, it just doesn't switch...
Any help would be greatly appreciated... I've looked at other posts but none address my exact problem or provide a working solution...

[/FONT][/COLOR]**EDIT**: My problem is exactly the same as described [here]("http://column80.com/api.v2.php?a=askubuntu&q=635349"), when I launch nvidia-settings in a terminal, I also get the error


```
ERROR: nvidia-settings could not find the registry key file. 
This file should have been installed along with this driver at
/usr/share/nvidia/nvidia-application-profiles-key-documentation. 
The application profiles will continue to work, but values cannot be
prepopulated or validated, and will not be listed in the help text. 
Please see the README for possible values and descriptions.
```
However the solutions proposed there, namely


```
cd /usr/share/nvidia
mv nvidia-application-profiles-340.76-key-documentation
nvidia-application-profiles-key-documentation
mv nvidia-application-profiles-340.76-rc nvidia-application-profiles-rc
```
(changing 340.76 in the number corresponding to the actual driver on my system of course)


refer to Ubuntu 15.04 (I'm on 16.04) and involve manually creating files, which has broken my system before so I'm reluctant to do so.

(P.S. I also asked this question [here on AskUbuntu]("http://askubuntu.com/questions/856208/cannot-switch-from-intel-to-nvidia-in-ubuntu-16-04-nvidia-prime"), will post solutions to either when found).

---

### Post by mc4man on 2016-12-11
There should be no reason why that card shouldn't work with nvidia-prime. As an example here on a 660m all is fine.
As far as nvidia-settings that file is a symlink to /etc/alternatives/nvidia... which is a symlink back to /usr/share/nvidia-367/.., see screen to possibly discern the convoluted paths.

Maybe try this - 
```
sudo apt purge nvidia*
```
Once that completes run this simulation, look thru carefully & if all seems proper run for real i.e., remove the -s
```
sudo apt -s autoremove
```
Then reboot & install nvidia-367, once it's installed reboot & see where you stand..

Edit - some screens *may* show up shortly, more forum nonsense... 

inxi-b in screen 2 shows nvidia working as the renderer

---

### Post by mc4man on 2016-12-11
............................................

---

### Post by bart.vanaudenhove on 2016-12-17
I did as you said, mc4man (very clear explanation by you BTW), but to no avail, still exactly the same problem...

---

### Post by matthew-maca on 2017-04-18
First of all, Sorry about the necro but,
i found a way to fix the key problem.
the keys are located in /usr/share/nvidia-vesrion
just move them to /usr/share/nvidia and remove the version number

---

