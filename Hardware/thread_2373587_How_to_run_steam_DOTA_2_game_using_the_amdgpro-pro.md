---
title: "How to run steam DOTA 2 game using the amdgpro-pro driver ?"
date: 2017-10-07
forum: Hardware
---

### Post by stefanoskikristijan on 2017-10-07
I am running Ubuntu 16.04.03 and i tried to play dota 2 with the standard AMD driver using in terminal:
```
DRI_PRIME=1 steam steam://rungameid/570
```
Which run the game but was very very laggy... So i installed the  amdgpu-pro driver but now when i run the game with the same command in terminal the AMD GPU doesnt even awake. I check that by using 'sensors' in terminal and it doesnt snow fan temp etc.. but it used to show before i installed the driver.
OUTPUT OF dpkg -l amdgpu-pro
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version           Architecture      Description
+++-=========================-=================-=================-========================================================
ii  amdgpu-pro                17.30-465504      amd64             Meta package to install amdgpu Pro components.


```
BTW i have Intel HD4000 and AMD HD8570. How can i use the AMD card with the gpu pro driver from amd to run DOTA 2 with the amd card ? I somehow managed it year ago when i had ubuntu but after that had a break from it using Windows and now i cannot manage it...

---

### Post by khoriam on 2017-10-12
Have you solved it?

---

