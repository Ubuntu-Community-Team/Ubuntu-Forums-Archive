---
title: "My CPU fan is acting strangely."
date: 2009-05-21
forum: Hardware
---

### Post by MadnessRed on 2009-05-21
My CPU fan suddenly, for no apparent reason just bursts on for a few seconds and then turns off. It very loud as I can't here my music over it, and very annoying. My CPU temperature is stable at arround 30-34&deg;C so the fan should be at a stable level. I tried installing fancontrol but it doesn't seem to have worked.

I am gonna try and create a log of fan speed an cpu temp to post...

> CPU Temp - Fan Speed
32 - 26% (arround 26% seems normal and it not audiable)
32 - 26%
32 - 26%
32 - 55% (arround 55% its clearly heard but is bearable)
32 - 41%
32 - 26%
32 - 26%
32 - 65%
32 - 68% (arround 70% its umlpeasently loud)
32 - 47%
32 - 26%
32 - 73%
32 - 74%
32 - 74%
32 - 51%
32 - 68%
32 - 68%
32 - 68%
32 - 68%
32 - 47%
32 - 26%
32 - 26%
32 - 26%
32 - 73%
32 - 50%
32 - 26%
32 - 26%
32 - 67%
32 - 75%
32 - 49%
32 - 26%
32 - 74%
32 - 80%
32 - 95%
32 - 63%
32 - 96%
32 - 101% (note 101% is possbile as I programmed a bit wrong, I divided fan speed by 5000 which I though was max but fan can do 5037)
32 - 101%
32 - 100%
32 - 47%
32 - 26%
32 - 26%
32 - 26%
32 - 101%
32 - 36%
32 - 26%
32 - 26%
32 - 74%
32 - 75%

Reading taken a 2 second intevals and got by the following code
[PHP]$s = explode("\n",shell_exec("sensors"));
$data = array();
foreach($s as $str){
	$t = explode(":",$str,2);
	if($t[0]){
		$data[$t[0]] = explode("(",$t[1]);
		$data[$t[0]] = idstring($data[$t[0]][0],true);
	}
}
unset ($s,$t,$str);[/PHP]

---

### Post by MadnessRed on 2009-05-21
ok, this is taking hte mick, so see how much good my cpu fan was doing I unplugged it an recorded the temperatures. And after unlpugging it, the CPU temperature went down!!! Then I plugged it back in and the CPU temp went up again.

> CPU Temp - Fan Speed
33 - 100% -- and uplug the fan.
33 - 0%
33 - 0%
33 - 0%
33 - 0%
33 - 0%
33 - 0%
33 - 0%
33 - 0%
33 - 0%
33 - 0%
33 - 0%
33 - 0%
33 - 0%
32 - 0%
32 - 0%
32 - 0%
32 - 0%
32 - 0%
32 - 0%
32 - 0%
32 - 0%
32 - 0%
32 - 0%
32 - 0%
32 - 0%
31 - 0%
31 - 0%
31 - 0%
31 - 0%
31 - 0%
31 - 0%
31 - 0%
31 - 0%
31 - 0%
31 - 0%
31 - 0%
31 - 0%
31 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0%
30 - 0% -- end of 5 mins
30 - 0%
30 - 0% -- plugged fan back in now.
30 - 0%
30 - 58%
30 - 0%
30 - 21%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
31 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 26%
32 - 102%
32 - 102%
33 - 102%
33 - 102%
33 - 102%


I did put the side of the case back on. And those reading were taken at 5 second intervals

---

### Post by MadnessRed on 2009-06-01
bump

---

