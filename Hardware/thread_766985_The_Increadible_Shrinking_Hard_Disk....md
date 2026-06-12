---
title: "The Increadible Shrinking Hard Disk..."
date: 2008-04-25
forum: Hardware
---

### Post by delsydebothom on 2008-04-25
My hard disk seems to be shrinking. I know this is strange, but between yesterday and today, I've gone from 3.4 GB free (and I went on a deleting spree just to accomplish that). I woke up today, and I have 0 bytes free; my wife can't even log into her profile, and I'm afraid that if I restart the computer, I won't be able to log into mine. 

Here is the strangest part: deleting files does not seem to be freeing up any space anymore. What is happening to my computer??

---

### Post by dstew on 2008-04-25
Try```
sudo apt-get clean
```to remove the downloaded packages of your installed programs. You can also do this from the synaptic window, in Settings --> Preferences --> Files --> Delete downloaded packages after installation. I think it will stay that way until you change it back, so it won't build up the cache again.

---

### Post by delsydebothom on 2008-04-25
> **dstew said:**
> Try```
sudo apt-get clean
```to remove the downloaded packages of your installed programs. You can also do this from the synaptic window, in Settings --> Preferences --> Files --> Delete downloaded packages after installation. I think it will stay that way until you change it back, so it won't build up the cache again.

I tried that, and it freed up 435.4 Mbs. However, I've been keeping my eye on it--now its down to 434.9 Mbs. :confused: This is getting really weird.

---

### Post by dstew on 2008-04-25
There are processes that create log files, and add to them every so often. You can look at your active processes using the **top** command. Maybe there is some process that is going crazy with its logs...look in the /var/log directory.

---

### Post by Mr_Congeniality on 2008-04-25
Wowsers.  That's freaking crazy.  If mine acts up I'll be sure to look into it further and let you know of the problem and possible solution(s).

---

### Post by delsydebothom on 2008-04-25
There are only 12.5 Megs of of logs right now. They number and size of the logs are staying the same, while my disk space keeps shrinking. :( I feel like everything I do is just delaying the inevitable.

---

### Post by kingpoiuy on 2008-04-25
Do a search for the largest file on your HDD.

In a terminal:
```
find -name '*' -size +1G
```


That will show you all your files over 1 GIG

Just a shot in the dark but if a single file is causing this issue then you can find it this way.

---

### Post by delsydebothom on 2008-04-25
I did have one file about a GB in size--a backup of some older files. But that wouldn't explain the continual shrinking, would it? I don't know, all I know is that I am losing about 1 megabyte every 20 minutes.

---

### Post by Terry of Astoria on 2008-04-25
What is the output from dmesg?
Type dmesg in the terminal to get diagnostic messages from the kernel.

---

### Post by Terry of Astoria on 2008-04-25
You can get more info by using 
```
du
```
and - or 
```
df
```
Just type ```
du
```
and hit enter
remember you can 
```
man du
```
if you want.

---

### Post by arsenic23 on 2008-04-25
Type baobab into your terminal and see if the disk usage analyzer can help you out.  ( I'm asuming your using Gnome - I think it's a part of Gnome. )  It will make a nice little graph of what's taking up space on your drive after you hit 'analyze disk'.


############## EDIT:
Oh, and you could also use: ```
sudo find / -cmin 20
``` to see what files have been modified in the last 20 minutes system wide.

---

### Post by delsydebothom on 2008-04-25
> **Terry of Astoria said:**
> What is the output from dmesg?
Type dmesg in the terminal to get diagnostic messages from the kernel.

When I type in dmesg, it says, *ahem*:

[184677.667478] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184683.659794] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184689.652166] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184695.644521] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184701.636897] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184707.629261] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184713.621604] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184719.613962] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184725.606325] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184731.598688] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184737.591100] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184743.583435] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184749.575771] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184755.568129] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184761.560490] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184767.552848] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184773.545215] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184779.537573] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184785.529938] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184791.522301] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184797.514656] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184803.507027] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184809.499381] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184815.491747] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184821.484117] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184827.476463] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184833.468830] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184839.461205] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184845.453553] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184851.445911] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184857.438271] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184863.430645] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184869.422995] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184875.415378] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184881.407711] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184887.400076] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184893.392446] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184899.384801] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184905.377161] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184911.369523] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184917.361885] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184923.354245] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184929.346625] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184935.338973] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184941.331331] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184947.323693] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184953.316055] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184959.308431] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184965.300773] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184971.293123] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184977.285502] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184983.277863] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184989.270233] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[184995.262580] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185001.254945] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185007.247303] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185013.239701] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185019.232014] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185025.224403] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185031.216749] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185037.209131] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185043.201465] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185049.193827] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185055.186188] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185061.178559] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185067.170929] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185073.163278] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185079.155641] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185085.147996] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185091.140362] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185097.132722] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185103.125079] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185109.117445] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185115.109804] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185121.102166] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185127.094539] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185133.086877] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185139.079259] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185145.071609] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185151.063970] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185157.056334] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185163.048691] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185169.041056] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185175.033419] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185181.025803] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185187.018135] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185193.010518] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185199.002864] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185204.995223] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185210.987606] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185216.979944] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185222.972327] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185228.964671] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185234.957026] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185240.949391] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185246.941781] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185252.934115] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185258.926471] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185264.918889] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185270.911199] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185276.903556] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185282.895932] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185288.888296] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185294.880662] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185300.873017] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185306.865435] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185312.857723] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185318.850115] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185324.842444] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185330.834806] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185336.827169] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185342.819531] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185348.811889] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185354.804249] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185360.796630] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185366.788979] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185372.781341] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185378.773697] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185384.766058] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185390.758419] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185396.750805] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185402.743141] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185408.735513] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185414.727869] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185420.720229] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185426.712590] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185432.704948] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185438.697304] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185444.689666] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185450.682030] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185456.674378] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185462.666752] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185468.659120] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185474.651474] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185480.643837] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185486.636198] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185492.628556] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185498.620933] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185504.613279] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185510.605645] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185516.598004] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185522.590370] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185528.582727] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185534.575108] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185540.567450] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185546.559798] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185552.552173] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185558.544530] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185564.536897] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185570.529253] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185576.521617] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185582.513993] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185588.506340] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185594.498701] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185600.491060] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185606.483422] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185612.475785] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185618.468144] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185624.460506] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185630.452872] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185636.445234] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185642.437594] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185648.429959] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185654.422313] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185660.414672] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185666.407035] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185672.399398] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185678.391754] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185684.384116] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185690.376482] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185696.368842] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185702.361201] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185708.353562] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185714.345943] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185720.338292] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185726.330653] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185732.323013] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185738.315370] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185744.307731] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185750.300090] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185756.292453] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185762.284813] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185768.277214] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185774.269539] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185780.261896] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185786.254261] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185792.246617] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185798.238982] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185804.231342] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185810.223704] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185816.216065] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185822.208428] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185828.200789] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185834.193147] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185840.185510] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185846.177870] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185852.170230] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185858.162592] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185864.154961] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185870.147318] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185876.139684] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185882.132037] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185888.124398] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185894.116766] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185900.109119] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185906.101480] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185912.093846] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185918.086204] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185924.078581] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185930.070948] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185936.063296] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185942.055669] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185948.048068] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185954.040392] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185960.032734] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185966.025098] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185972.017459] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185978.009823] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185984.002179] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185989.994557] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[185995.986924] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186001.979261] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186007.971631] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186013.964001] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186019.956347] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186025.948719] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186031.941073] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186037.933433] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186043.925791] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186049.918195] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186055.910516] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186061.902875] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186067.895235] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186073.887603] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186079.879957] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186085.872317] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186091.864684] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186097.857041] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186103.849393] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186109.841766] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186115.834123] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186121.826485] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186127.818849] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186133.811211] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186139.803593] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186145.795931] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186151.788295] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186157.780655] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186163.773013] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186169.765397] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186175.757746] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186181.750112] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186187.742457] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186193.734824] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186199.727185] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186205.719545] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186211.711907] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186217.704265] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186223.696628] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186229.688988] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186235.681352] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186241.673716] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186247.666075] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186253.658437] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186259.650795] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186265.643163] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186271.635515] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186277.627881] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186283.620237] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186289.612601] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186295.604961] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186301.597312] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186307.589686] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186313.582046] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186319.574406] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186325.566787] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186331.559131] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186337.551499] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186343.543856] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186349.536223] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186355.528576] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186361.520937] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186367.513304] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186373.505657] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186379.498019] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186385.490407] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186391.482739] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186397.475104] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186403.467462] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186409.459824] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186415.452186] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186421.444552] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186427.436930] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186433.429271] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186439.421632] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186445.413998] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186451.406353] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186457.398727] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186463.391089] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186469.383435] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186475.375809] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186481.368175] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186487.360548] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186493.352886] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186499.345241] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186505.337603] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186511.329995] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186517.322330] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186523.314688] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186529.307050] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186535.299407] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186541.291779] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186547.284131] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186553.276480] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186559.268868] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186565.261232] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186571.253836] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186577.245963] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186583.238295] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186589.230658] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186595.223023] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186601.215380] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186607.207737] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186613.200107] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186619.192475] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186625.184828] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186631.177184] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186637.169544] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186643.161907] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186649.154266] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186655.146630] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186661.138994] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186667.131353] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186673.123714] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186679.116078] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186685.108434] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186691.100789] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186697.093168] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186703.085519] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186709.077905] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186715.070240] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186721.062602] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186727.054966] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186733.047327] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186739.039690] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186745.032056] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186751.024409] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186757.016768] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186763.009136] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186769.001492] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186774.993854] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186780.986214] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186786.978575] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186792.970939] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186798.963299] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186804.955659] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186810.948019] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186816.940385] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186822.932753] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186828.925103] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186834.917470] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186840.909825] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186846.902188] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186852.894550] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186858.886911] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186864.879272] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186870.871633] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186876.863995] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186882.856361] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186888.848715] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186894.841076] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186900.833441] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186906.825800] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186912.818163] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186918.810520] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186924.802885] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186930.795241] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186936.787605] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186942.779971] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186948.772329] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186954.764690] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186960.757059] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186966.749412] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186972.741773] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186978.734134] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186984.726495] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186990.718847] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[186996.711218] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187002.703582] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187008.695942] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187014.688300] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187020.680663] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187026.673026] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187032.665389] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187038.657745] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187044.650109] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187050.642472] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187056.634829] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187062.627198] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187068.619561] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187074.611913] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187080.604273] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187086.596637] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187092.589000] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187098.581366] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187104.573719] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187110.566082] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187116.558443] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187122.550802] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187128.543166] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187134.535525] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187140.527880] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187146.520244] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187152.512609] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187158.504971] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187164.497330] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187170.489693] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187176.482053] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187182.474417] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187188.466776] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187194.459138] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187200.451499] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187206.443859] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187212.436223] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187218.428587] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187224.420944] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187230.413305] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187236.405675] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187242.398029] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187248.390380] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187254.382760] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187260.375113] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187266.367475] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187272.359836] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187278.352196] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187284.344557] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187290.336921] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187296.329280] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187302.321643] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187308.313998] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187314.306361] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187320.298725] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187326.291084] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187332.283452] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187338.275809] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187344.268167] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187350.260531] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187356.252879] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187362.245250] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187368.237615] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187374.229976] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187380.222334] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187386.214695] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187392.207058] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187398.199419] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187404.191781] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187410.184140] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187416.176501] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187422.168864] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187428.161226] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187434.153586] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187440.145958] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187446.138311] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187452.130670] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187458.123022] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187464.115389] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187470.107755] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187476.100117] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187482.092479] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187488.084838] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187494.077200] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187500.069561] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187506.061921] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187512.054280] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187518.046646] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187524.039005] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187530.031369] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187536.023733] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187542.016089] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187548.008452] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187554.000811] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187559.993171] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187565.985531] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187571.977892] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187577.970253] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187583.962607] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187589.954981] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187595.947388] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187601.939721] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187607.932085] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187613.924471] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187619.916786] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187625.909164] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187631.901508] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187637.893870] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187643.886231] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187649.878597] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187655.870976] ACPI: Unable to turn cooling device [d9ca8f18] 'on'
[187661.863322] ACPI: Unable to turn cooling device [d9ca8f18] 'on'

---

### Post by savagenator on 2008-04-25
woah, sounds like a decompression bomb gone wild, or even a linux virus! 

the strange thing is that the output you gave out points too acpi problems, and you should boot with acpi=off for your kernel. BUT that doesn't seem like what would likely cause the problem...

So like I said, hopefully something didn't go corrupt and rearange its bits into a decompression bomb or something.

---

### Post by savagenator on 2008-04-25
woah, sounds like a decompression bomb gone wild, or even a linux virus! 

the strange thing is that the output you gave out points too acpi problems, and you should boot with acpi=off for your kernel. BUT that doesn't seem like what would likely cause the problem...

So like I said, hopefully something didn't go corrupt and rearange its bits into a decompression bomb or something.

---

### Post by delsydebothom on 2008-04-25
> **savagenator said:**
> woah, sounds like a decompression bomb gone wild, or even a linux virus! 

the strange thing is that the output you gave out points too acpi problems, and you should boot with acpi=off for your kernel. BUT that doesn't seem like what would likely cause the problem...

So like I said, hopefully something didn't go corrupt and rearange its bits into a decompression bomb or something.

How would I go about booting Ubuntu with the acpi off? And what would that affect?

---

### Post by dstew on 2008-04-25
Add **acpi=off** to the end of the kernel line in /boot/grub/menu.lst

---

### Post by DragonHawk on 2008-04-28
This appears to be an issue with certain hardware.  Details are unclear.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63550](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63550)

If you prefer, rather than disabling ACPI completely, you can blacklist the "thermal" and/or "fan" kernel modules .  That will prevent the kernel from trying to control the fan.  To do so, edit the file "/etc/modprobe.d/blacklist" (using sudo), and add a line "blacklist thermal" or "blacklist fan", as appropriate.

Note that if your system actually *needs* the kernel to be able to control the fan (to prevent system overheat), blacklisting the modules may cause system instability or hardware damage.  In my case, the fans were working, despite the log messages saying the kernel could not turn them on.

---

### Post by nuke_fluke on 2008-04-28
It may not be of much use....
But this happened once to my windows Vista.
i tried to enhance the resolution of a video file by using 'Video Enhancer' software and after some moments the file became 4 GB big (from 40 MB) and it was still increasing..
Even I could not delete it So I had to format that drive...
I ran out of disk space and was on the verge of sth really  bad....:)

But after formatting that drive and uninstalling the software,everything was alright...

---

### Post by zach382 on 2008-04-29
Use the "disk usage analyzer" in the accessories menu. You should be able to easily find the biggest files/folders.

edit: saw it got mentioned before.

---

### Post by delsydebothom on 2008-04-29
> **DragonHawk said:**
> This appears to be an issue with certain hardware.  Details are unclear.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63550](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63550)

If you prefer, rather than disabling ACPI completely, you can blacklist the "thermal" and/or "fan" kernel modules .  That will prevent the kernel from trying to control the fan.  To do so, edit the file "/etc/modprobe.d/blacklist" (using sudo), and add a line "blacklist thermal" or "blacklist fan", as appropriate.

Note that if your system actually *needs* the kernel to be able to control the fan (to prevent system overheat), blacklisting the modules may cause system instability or hardware damage.  In my case, the fans were working, despite the log messages saying the kernel could not turn them on.

Thank you, that fixed the problem! In fact, I now have over 20 Gigs of free space!! :)

---

