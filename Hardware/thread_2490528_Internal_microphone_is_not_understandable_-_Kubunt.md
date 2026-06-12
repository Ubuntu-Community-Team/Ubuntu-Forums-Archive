---
title: "Internal microphone is not understandable - Kubuntu 23.04"
date: 2023-09-06
forum: Hardware
---

### Post by nador2 on 2023-09-06
Hello, I have lenovo yoga 300-11bdy, Kubuntu 23.04.

My microphone was doing only some noise - when I tried to monitor level  according my speach, it was without reaction, still same level when I  speak or I am loud. People in conferences with me said that they can  hear themselves when they spoke, but not me (sounds like some feedback).
I have no idea how works external microphone - I have no such device for checking.

 I have this realtec:

```
[FONT=monospace][COLOR=#000000]cat /proc/asound/card*/codec* | grep Codec [/COLOR]
[/FONT]
```

```
[FONT=monospace]
[COLOR=#ff5454]**Codec**[/COLOR][COLOR=#000000]: Realtek ALC236 [/COLOR]
[COLOR=#ff5454]**Codec**[/COLOR][COLOR=#000000]: Intel Valleyview2 HDMI[/COLOR]
[/FONT]
```

I found solution -** install pavucontrol and mute one or second side of microphone**. They wrote that this was helpful with Lenovo computers.Result in my case is - **I am already hearable in conferences, but very very bad sound - weak, quiet, like in bathroom, not understandable.**  I tried to adjust by volume levels, but everything above or under 100  percent of this one side of microphone was not working. It was without  difference if I tried left or right side to mute and second I tried to  adust - both was the same result "quiet in bathrooom". Its so bad that  even we are only two and I try to have loud voice, the second person can  not understand me almost any word. And the feedback of their voice  remains.


Here is recording of the feedback of person who recorded (beginning) and  terrible sound of me (rest of video): [https://youtu.be/m0WOZO2fAJQ](https://youtu.be/m0WOZO2fAJQ)

Thank you very much for your advices what to try. (I wanted to add screenshot of pavucontrol and alsamixer, but it was avoided by forum).

---

### Post by TheFu on 2023-09-08
Please use the "thread tools" button to mark this thread as **SOLVED**, if it is solved. Save others time.

Microphones have gain controls. You should practice recording using **parec** or **parecord** to get the recording levels correct for your specific equipment.  There's no button for "setup microphone to be perfect", sorry.

---

### Post by nador2 on 2023-09-10
> **TheFu said:**
> Please use the "thread tools" button to mark this thread as **SOLVED**, if it is solved. Save others time.

Microphones have gain controls. You should practice recording using **parec** or **parecord** to get the recording levels correct for your specific equipment.  There's no button for "setup microphone to be perfect", sorry.

I need web telecomunication with Jitsi, Skype, etc.How can parec or parecord help me?

Is there any chance to set up microphone in whole system, not only in parec or parecord?

I guess Linux is also usable for telecomunication, so there have to be way how to set up microphone.

---

### Post by TheFu on 2023-09-10
> **nador2 said:**
> I need web telecomunication with Jitsi, Skype, etc.How can parec or parecord help me?

Is there any chance to set up microphone in whole system, not only in parec or parecord?

I guess Linux is also usable for telecomunication, so there have to be way how to set up microphone.

You start with the simple stuff, before getting into the crap that GUI programs use. This way, you'll know whether it is something like hardware that is failing or the complexities of MSFT or webRTC breaking audio.

Basic troubleshooting:
* simplify
* test
* repeat

We can't start flying a 4 engine aircraft when we aren't experts.  We have to start in a glider, then move to a single engine plane first. See the analogy?

---

### Post by nador2 on 2023-09-12
> **TheFu said:**
> You start with the simple stuff, before getting into the crap that GUI programs use. This way, you'll know whether it is something like hardware that is failing or the complexities of MSFT or webRTC breaking audio.

Basic troubleshooting:
* simplify
* test
* repeat

We can't start flying a 4 engine aircraft when we aren't experts.  We have to start in a glider, then move to a single engine plane first. See the analogy?

OK, so you said I have to try parec or parecord. When I try parec in console, I get smething what I completely dont know what is it:

```
[FONT=monospace][COLOR=#000000]&#65533;&#65533;N&#65533; [/COLOR]
&#65533;&#65533;Õ&#547;&#65533;&#65533;&#65533;&#65533;&#65533;&&#65533;=3&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;J&#65533;&#9618;&#65533;&#65533;&#65533;K&#65533;&#65533;&#65533;&#65533;&#65533;j&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#947;M&#65533;&#65533;&#65533;&#65533; 
                                                    &&#65533;  y&#65533;yH&#65533;j&#65533; 
                                                               F&#9618;&#65533;]j3&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;i&#65533;&#65533;&#65533; &#65533;X&#65533;&#65533;&#65533;&#65533;&#65533;I&#65533;p1]W&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;1{&#65533;&#65533;&#65533;&#65533;3s1&#65533;&#65533;&#65533;&#65533;yP&#65533;HoXCPha:&#65533;2AM<G&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V&#65533;s&#65533;&#65533;&#65533;&#65533;k:{YX&#65533;*CM&#65533;&#65533;J&#65533;_ &#65533;G&#65533;
&#65533;&#65533;&#65533;]&#65533;T&#65533;^&#65533;P[&#65533;Q&#65533;'&#65533;$&#65533;1a\&#65533;T&#65533;&#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;       &#65533;"&#65533;&#65533;&#65533;|&#65533;&#65533;&#9618;&#65533;&#65533;z&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;v&#65533;mx[x2&#65533;']^fAz&#65533;&#65533;&#65533;C&#65533;&#65533;&#65533;d&#65533;&#9618;&#65533;&#65533;&#65533;&#65533;&#65533;{1&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;`&#65533;fDFS&#65533;&#65533;4}&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;q!S&#65533;|&#65533;
3 
 7&#65533;~&#65533;&#65533;&#65533;%e&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;[*&#65533;l&#65533;^&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;_&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; 
                                            &#65533;&#65533;&#65533;b&#65533;&#65533;n&#65533;M&#65533;o&#65533;&#65533;t&#65533;E&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;#|&#65533;&#65533;"w&#65533;n&#65533;&#65533;$&#65533;&#65533;[#+ 
                                                                                    &#65533;U(d&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;G&#65533;U?R&#65533;&#65533;&#65533;&#65533;+VN[&#65533;h&#65533;&#65533;|&#65533;&#65533;&#65533;&#65533;GoI&#65533;&#65533;gd&#65533;<C&#9618;&#65533;I&#9618;R&#65533;&#65533;v&#65533;&#65533;{&#65533;r&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;Fy 
w&#65533;&#65533;R&#65533;7RI&#65533;@qf79&#65533;&#65533;&#65533;Dri&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;r0h&#65533;&#65533;&#65533;&#9618;w#9,&#65533;&&#65533;Z&#65533;Sd;&#9618;A-<&#65533;&#65533;&#65533;V&#65533;p:tXnv&#65533;EfE&#65533;k&#65533;x7;&#65533;0tTiak|&#65533;o&#65533;>P&#9618;s&#65533;&#9618;@I&#65533;<      5tT&#65533;&#65533;g&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;8&#65533;_&#65533;eh&#65533;O&#65533;jZZ&#65533;*&#65533;c&#65533;pyD&#65533;E6|&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;'k&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;K&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;&#65533;(&#65533;J&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;b&#65533;_&#65533;9&#65533;@gs&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;{&#65533;&#65533;&#65533;&#65533;J<Uj=&#65533;m&#65533;&#65533;~yv]c?&#65533;&#65533;r&#65533;%,&#65533;?/h.&#65533;8&#65533;\3J&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;9l
&#65533;&#65533;&#65533;&#1401;J&#65533;&#65533;&#65533;&#65533;1&#65533;&#65533;&#65533;$&#65533;\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;2&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;*aj3&#65533;&#65533;C&&#65533;&#65533;&#1166;&#65533;&#65533;f&#65533; &#65533;&#65533;&#65533;u&#65533;&#65533;&#65533;&&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;m&#65533;]&#65533;vi&#65533;p&#65533;k&#65533;&#65533;&#65533;&#65533;Ey&.#F&#65533;k&#65533;`h&#65533;:n^&#65533;&#65533;&#9618;=@>&#9618;&#65533;&#65533;&#65533;&#65533;s&#65533; 
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;/&#65533;m&#65533;&#65533;&#65533;&#65533;&#9618;&#65533;&#65533;  &#65533;&#65533;&#65533;&#65533;;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;/&#65533;Y&#65533;H&#65533;.4&#65533;@&#65533;&#65533;CQ&#65533;&#65533;N&#65533;E&#65533;&#610;&#65533;&#65533;&#65533;&#65533;c&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;*&"&#65533;'&#65533;    &#65533;&#65533;W&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;#&#65533;9&#65533;m&#65533;O&#65533;#&#65533;&#65533;&#65533;]&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^&#65533;0&#65533;Y&#65533;&#65533;2&#65533;5&#65533; UH4&#65533;}&#65533;&#65533;\g&#65533;3&#65533;&#65533;h&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;>&#65533;&#65533;&#65533;&#65533;T&#65533;&#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;L&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;L&#65533;8&#65533;&#65533;&#65533;q&#65533; 
                                                b-,[BmP&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;'&#65533;&#65533;>8&#65533;%&#65533;i&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;[&#65533;p&#65533;m&#65533;&#65533;&#65533;G&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Q&#65533;8&#65533;&#9618;&#65533;&#65533;@9&#65533;K&79j 
PY&#65533;4&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#999;J&#65533;E[COLOR=#000000]&#65533;&#1759;[/COLOR][COLOR=#000000]&#65533;&#65533;&#9618;&#65533;m`^&#65533;Es9-w;}&#65533;&#65533;&#65533;&#65533;&#65533;wg~~r&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;_&#65533;Q"H&&#65533;V&#9618;<&#65533;&#9618;`>&#65533;q&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;L\e&#65533;O&#65533; [/COLOR]
                                                                                                     &#65533;&#65533;&#65533;4&#65533;&#65533;&#65533;Z&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;&#65533;&#65533;f&#65533;&#65533;&#65533;&#65533;g&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#962;m&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;):\&#65533;q&#65533;0&#65533;#3r~ 
h&#9618;L&#65533;:&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;2&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;O&#65533;&#65533;&#65533;&#65533;&#65533;&#263;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;(&#65533;&#65533;&#65533;r&#65533;&#65533;&#65533;&#65533;&#65533;U&#65533;<.|,&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;t&#65533;S&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;-=6AD&#65533;-#(O&#65533;h&#65533;e&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;pX&#65533;&#65533;;\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;ba&#65533;q}&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=vK]c7&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;N&#65533;&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;v&#65533;
#,&#65533;#&#65533;                                                                                                               &#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;u&#65533;&#65533;&#65533;m&#65533;&#65533;&#65533;U&#65533;f&#65533;&#9618;&#65533;&#323;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1357;&#65533;(&#65533;&#65533;&#65533;5&#65533;`&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;_&#65533;&#65533;&#65533;&#65533;N#8+&#65533;&#65533;Q&#65533;&#65533;&#65533;&#65533;&#65533;B 
                     &#65533;&#65533;&#65533;&#65533;&#65533;$"&#65533; 
                             _F&#65533;@2&#65533;c&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;o&#65533;ll7\i 
&#65533;&#65533;PD&#65533;.u 
       &#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#9618;u 
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;+&#65533;r&#65533;i&#65533;&#65533;&#65533;:&#65533;s)%&#65533;&#65533;&#65533;&#65533;&i$&#65533;&#65533;&#65533;&#65533;&#65533;9&#65533;:m&#65533;5&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;X=K&#65533;&#65533;&#65533;&#1228;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;i&#65533;_&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;}+Y%[&#65533;H&#65533;#&#65533;&#65533;&#65533;&#65533;&#65533; 
-&#65533;S&#65533;&#65533;&#65533;&#65533;&#65533;j&#65533;&#9618;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;J&#65533;O&#65533;&#65533;&#65533;W&#65533;&#65533;&#65533;&#1193;&#65533;&#65533;]&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;6&#65533;&#65533;&#65533;&#65533;&#65533;/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;o&#65533;&#65533;&#65533;F&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;N&#65533;&#65533;j&#65533;S&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1496;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1308;&#65533;&#65533;&#65533;c&#65533;D&#65533;@&#65533;;&#65533;i&#65533;&#65533;&#65533;&#65533;&#65533;"&#65533;(e 
                                                                                                           &#65533;3&#65533;MFD&#65533;$&#65533;&#65533;&#65533;r]#Ho0&#65533;&#65533;&#65533;&#65533;&#65533;6&#65533;Q&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;otQ&#65533;&a&#65533;&#65533;&#65533;&#65533;h&#65533;&#1136;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;?&#65533;D&#65533;R`we]C&#65533;a&#65533;&#65533;&#65533;n&#65533;R 
&#65533;+>&#65533;U&#65533;}&#65533;V&#65533;r0Y&#65533;"(&#65533;&#65533;&#65533;Q&#65533;\&#65533;&#924;&#65533;_&#65533;:&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;q&#65533;&#65533;\&#65533;&#65533;&#65533;O&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;v&#65533;&#65533;&#65533;N&#65533;&#65533;&#65533;m&#65533;%&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;.&#65533;f&#65533;&#65533;&#65533;&#65533;N&#65533;}&#65533;&#65533;&#65533;:&#65533;k&#65533;&#65533; 
a>c}3&#65533;&#65533;&#65533;)&#65533;&#65533;&#65533;&#65533;&#65533;a&#65533;&#65533;&#65533;r&#65533;L&#65533;&#65533;7/&#9618;X+d&#65533;;&#65533;i&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;n&#65533;YqLuY&#65533;=&#65533;.&#65533;M&#65533;)f&#65533;X# 41+&#65533;9&#65533;Z&#65533;`&#65533;&#65533;&#9618;U&#65533;&#65533;&#65533;D&#65533;&#65533; &#65533;X&#65533;&#65533;8E&#65533;&#65533;&#65533;&#65533;&#65533;G&#65533;g&#65533;&#65533;8&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;E&#65533;&#65533;&#65533;&#1806;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;&#65533;&#65533;6&#65533;W&#65533;&#65533;&#65533;&&#65533;&#65533;&#65533;&#65533;&#9618;&#65533;&#65533;&#65533;&#65533; 
                                                                                                                                              \&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;3&#65533;A&#65533;&#65533;&#65533;d&#65533;Z&#65533;O&#65533;g&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;q&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;_&#65533;F&#65533;&#65533;&#65533;&&#65533;[&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;1&#65533;&#65533;&#65533;\&#65533;&#65533;&#65533;&#65533;D&#65533;&#65533;&&#65533;&#65533;&#65533;C&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;|&#65533;k&#65533;&#65533; 
'&#65533;&#65533;&#65533;&#65533;7'6&#65533;&#65533;:&#65533;&#404;<&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;$&#65533;&#9618;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; 0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;)o*&#65533;M1K&#65533;&#65533;&#65533;&#65533;&#65533;E&#65533;&#65533;&#65533;&#65533;N&#65533;;5G&#65533;T&#65533;4&#65533;g&#65533;}&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;WY&#65533;@&#65533;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;R&#65533;&#65533;&#65533;a&#65533;&#65533;4U=<;T9u<5IN&#65533;==T&#65533;@&#65533;&#65533;&#65533;|&#65533;&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;<&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=C &#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;5&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;C&#65533;+&#65533;&#65533;&#65533;C&#65533;&#725;&#1233;&#65533;'&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#896;&#65533;:&#65533;&#65533;&#65533;&#65533;&&#9618;)~!D60&#65533;P&#65533;H&#65533;2&#65533;LB}&#65533;&#65533;&#65533;&#65533;&#9618;H&#65533;&#65533;p&#65533;&#65533;&#65533;[COLOR=#000000]&#65533;&#1613;[/COLOR][COLOR=#000000]&#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;.&#65533;L&#65533;R&#65533;Y&#65533;@&#65533;Z&#65533;:&#65533;/&#65533; [/COLOR]
                                                                                                                                                               &#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;&#65533;&#65533;&#1659;&#65533;&#65533;&#65533;9&#65533;        &#65533;&#65533;&#65533;&#65533;


[/FONT]
```

When i use parecord, I get this:

```
[FONT=monospace][COLOR=#000000]Selhalo otev&#345;ení zvukového souboru.[/COLOR][/FONT]
```

In English somethink like "Opening of sound file failed."

So please, what is idea of this test? What should I do next? Thank you.

---

### Post by TheFu on 2023-09-12
Seems you didn't use the command as required.  Did you look up examples for how to use the command?

```
# ###############[ Pulse recording ]###################
# Record from named device - and convert to ogg.
$ **parec** -d alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo \ 
   | oggenc -b 192 -o foo.ogg --raw -

# Record from named device to .wav
$ **parecord**     -d     alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo    -r   saved.file.wav

```

Obviously, you'll need to specify the correct microphone device connected to your system.  I have a Logitech C920 webcam in the examples above. 
```
$ pactl list short sources 
```
will show the names, if any are connected and active.

Looking at the parec command above, it looks like the output is sent to stdout by default, so you are expected to redirect that to a file to be saved or to another command for encoding. I use **oggenc** above, but you can use any format you like. Up to you.

---

### Post by nador2 on 2023-09-12
> **TheFu said:**
> Seems you didn't use the command as required.  Did you look up examples for how to use the command?

```
# ###############[ Pulse recording ]###################
# Record from named device - and convert to ogg.
$ **parec** -d alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo \ 
   | oggenc -b 192 -o foo.ogg --raw -

# Record from named device to .wav
$ **parecord**     -d     alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo    -r   saved.file.wav

```

Obviously, you'll need to specify the correct microphone device connected to your system.  I have a Logitech C920 webcam in the examples above. 
```
$ pactl list short sources 
```
will show the names, if any are connected and active.

Looking at the parec command above, it looks like the output is sent to stdout by default, so you are expected to redirect that to a file to be saved or to another command for encoding. I use **oggenc** above, but you can use any format you like. Up to you.

Sorry, I am not programator, but end user. So I made:

```
[FONT=monospace][COLOR=#000000]$ pactl list short sources [/COLOR]
96      alsa_output.pci-0000_00_1b.0.analog-stereo.monitor      PipeWire        s32le 2&#8239;ch 48000&#8239;Hz     SUSPENDED 
97      alsa_input.pci-0000_00_1b.0.analog-stereo.3     PipeWire        s32le 2&#8239;ch 48000&#8239;Hz     RUNNING[/FONT]
``` 

Then I run

```
[FONT=monospace][COLOR=#000000]parec -d alsa_input.pci-0000_00_1b.0.analog-stereo.3 \    | oggenc -b 192 -o foo.ogg --raw - [/COLOR]
Kóduji standardní vstup do  
       "foo.ogg"  
p&#345;i pr&#367;m&#283;rné bitrate 192 kb/s (VBR kódování povoleno) 


Kódování souboru "foo.ogg" hotovo 

        Délka souboru:  0m 00,0s 
        Strávený &#269;as: 0m 00,0s 
        Pom&#283;r:        0,0000 
        Pr&#367;m&#283;r bitrate:  inf kb/s

[/FONT]
```

Then I run

```
[FONT=monospace][COLOR=#000000]parecord -d alsa_input.pci-0000_00_1b.0.analog-stereo.3 -r   saved.file.wav[/COLOR][/FONT]
```[FONT=monospace]

I had to interrupt with [/FONT][FONT=monospace][COLOR=#000000]^C[/COLOR] and I have no idea where I can find this wav to check what it sounds.

So probably I made something wrong again.
[/FONT]

---

### Post by TheFu on 2023-09-12
End-users have been using the UNIX shell since the 1970s.  Nothing suggested is "programming" or even advanced stuff.  It is for end-users.

BTW, technically, the "console" is when there isn't any GUI at all and it was connected using a serial cable (and still is).  If you use a terminal, understand that there are 20-50 different terminal programs and that you can have as many of them running concurrently as you like/need.

I'm sorry, I only understand English so any error messages aren't understood in non-English languages. Well, I do know some Japanese, German, and Spanish, but not the language above. I'm not fluent in any of those.

I'm guessing the first parec complaint is that oggenc doesn't exist?  The example I showed used 2 commands, piping the output from the first into the 2nd.  This is a very common thing. Heck, MS-DOS supported it as does MS-Windows and all Unix-like OSes.  [https://www.youtube.com/watch?v=tc4ROCJYbm0](https://www.youtube.com/watch?v=tc4ROCJYbm0) is an explanation by AT&T in 1982 about the beginnings of UNIX. This is over 10 yrs after it was a popular OS in telecommunications.  Pretty much every OS you will touch will have the foundations set by this OS, UNIX, so understanding just a little about it is useful for anyone trying to use Linux or MS-Windows or MacOS or CPM or ... pretty much any desktop OS.

The **parecord** saved the output to the file you specified, "saved.file.wav".  Because no directory was specific, it would save it to the CWD where the terminal session was at the time. That is likely your $HOME directory.  If you try to play that file, you should hear whatever the microphone picked up.  If it didn't capture any noises, perhaps the microphone gain was too low?  Or the speaker volume is set to low or muted.   Try again with the gain set higher for both and ensure the speakers aren't muted.

---

### Post by nador2 on 2023-09-13
> **TheFu said:**
> End-users have been using the UNIX shell since the 1970s.  Nothing suggested is "programming" or even advanced stuff.  It is for end-users.

BTW, technically, the "console" is when there isn't any GUI at all and it was connected using a serial cable (and still is).  If you use a terminal, understand that there are 20-50 different terminal programs and that you can have as many of them running concurrently as you like/need.

I'm sorry, I only understand English so any error messages aren't understood in non-English languages. Well, I do know some Japanese, German, and Spanish, but not the language above. I'm not fluent in any of those.

I'm guessing the first parec complaint is that oggenc doesn't exist?  The example I showed used 2 commands, piping the output from the first into the 2nd.  This is a very common thing. Heck, MS-DOS supported it as does MS-Windows and all Unix-like OSes.  [https://www.youtube.com/watch?v=tc4ROCJYbm0](https://www.youtube.com/watch?v=tc4ROCJYbm0) is an explanation by AT&T in 1982 about the beginnings of UNIX. This is over 10 yrs after it was a popular OS in telecommunications.  Pretty much every OS you will touch will have the foundations set by this OS, UNIX, so understanding just a little about it is useful for anyone trying to use Linux or MS-Windows or MacOS or CPM or ... pretty much any desktop OS.

The **parecord** saved the output to the file you specified, "saved.file.wav".  Because no directory was specific, it would save it to the CWD where the terminal session was at the time. That is likely your $HOME directory.  If you try to play that file, you should hear whatever the microphone picked up.  If it didn't capture any noises, perhaps the microphone gain was too low?  Or the speaker volume is set to low or muted.   Try again with the gain set higher for both and ensure the speakers aren't muted.

OK, I found the file and it looks the same bad as the video i shared (first Youtube above). Its boosted, also you can see some noise when should be silence (not speaking). But in Youtube video above is communication betweem two users and video vas captured from the second user and my computer made in adition to boosting also feedback of his voice.. For me it looks that something is wrong and the sound goes somewhere where it should not go.. Or something like this - i dont know. 

Parecord record: [https://youtube.com/shorts/g7Ugbfc0Gro?feature=share](https://youtube.com/shorts/g7Ugbfc0Gro?feature=share)

---

### Post by TheFu on 2023-09-13
Keeping it simple.   Have you used the **pavucontrol** tool to check the inputs, gains and volume? It isn't installed by default.  If you stay simple, it is easier to troubleshoot. parec and pacmd are part of pulse audio. Using them removes the unknown, added, complexities of webRTC and whatever MSFT thinks is correct.

The 2nd YT sounds like there's a connection issue with the microphone AND that the gain it too high. pavucontrol provides controls to handle the gain, but the connection may be a hardware issue. An external USB mic may be needed to avoid the internal issues.  With laptops, getting a mic that works with the 2.5mm jack can be problematic, since there are 3 different standards and which your laptop uses isn't something I'd know. 

All the 2.5mm microphone jacks look the same. Just easier to go with a USB mic.  Start thinking about that.  If you decide, I can recommend one, but it is $40.  I have a number of different mics. 2 use 2.5mm jacks and 2 use USB connections.  The 2.5mm analog mics are easy to break and harder to figure out the settings for, IME.  Whereas a USB mic, provided it is supported, just works. Also, the vendor name usually shows up in the list of devices in all the audio tools, clearly. No guessing which is what. Of course, people will sell you more expensive mics.  I wanted something better than normal, but not radio/professional costs.  

There are mono lapel mics for $6 for a pack of 4. I've actually had good luck with them, but they were harder to configure and if the problem is with the internal audio chip support, it won't be any better.

The feedback in the jitsi recording is because someone's speakers are too loud and their microphone it picking that up too.  With jitsi, it is often useful to mute everyone who isn't talking. There's a button for that.  The last few weeks, Jitsi has been making some fairly large changes behind the scenes.  For example, they just switched from h.264 to h.265 (vp9) as their default video codec which makes everything harder for older computers and 4+ yr old android devices that don't have h.265 decoding built in.  They have some other plans that could make older computers not work at all.  I think they broke their AppImage jitsi meet app over the weekend too.  My LUG uses jitsi meet for multiple meetings each week.  When people have sound issues, we troubleshoot using chat and regular telephones.

Of course, you could google for "scratchy mic ubuntu Realtek ALC236"    [https://www.reddit.com/r/linuxquestions/comments/11x3s4o/audio_issues_realtek_alc236/](https://www.reddit.com/r/linuxquestions/comments/11x3s4o/audio_issues_realtek_alc236/) was found. Seems they are all HP users, but with the same audio chip.  One guy got a 6.3.x kernel working, so you may want to try the 23.10 beta (don't install it, just run it in a "Try Ubuntu" mode to see if it works better.

---

