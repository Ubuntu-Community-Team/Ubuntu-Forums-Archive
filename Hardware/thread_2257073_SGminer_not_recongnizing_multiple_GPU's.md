---
title: "SGminer not recongnizing multiple GPU's"
date: 2014-12-16
forum: Hardware
---

### Post by aquechipa on 2014-12-16
[IMG]http://engine.adzerk.net/i.gif?e=eyJhdiI6NDE0LCJhdCI6NCwiY20iOjk1NTYwLCJjaCI6MTY1MzEsImNyIjoyNjY1NjMsImRpIjoiZDFiNGExZTRjNTM2NGFkYmFmMTc2ZTVmNjQ1MGM4MTYiLCJkbSI6MSwiZmMiOjMzMDkyMCwiZmwiOjE3MTc0MSwiaXAiOiIxODcuMTc2LjIyNy4yNTMiLCJrdyI6ImdwdSxjZ21pbmVyLHgtdXNlci1yZWdpc3RlcmVkLHgtY29tbXVuaXR5LHgtbmV3c2xldHRlcix4LWhvc3QtYXNrdWJ1bnR1LmNvbSIsIm53IjoyMiwicGMiOjAsInByIjo1NzIyMiwicnQiOjEsInJmIjoiaHR0cDovL2Fza3VidW50dS5jb20vdXNlcnMvMzU1MzQ2L2hhcnVtaS1raXJvc2F3YSIsInN0Ijo1Njc0OSwidWsiOiJ1ZTEtODA5YzFhZjQyYjk1NDZjNWE5MzkzN2Y3YjgxODM2NjEiLCJ6biI6MjksInRzIjoxNDE4NzYwNTM4MzQ3LCJiZiI6dHJ1ZX0&s=W2C8xtmFGSxG8epftPFeEmxUJyU[/IMG]
    [TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]                I'm not being able to mine with my 4 GPU's; I'm only being  able to mine with my GPU that is connected to the monitor. When I run > sgminer -n in the terminal it recognizes 1 GPU max. I've already tried changing the xorg conf with > sudo aticonfig -f --adapter=all --initial, and still nothing. Then I followed this post [How do I use multiple AMD graphic cards?]("http://askubuntu.com/questions/264266/how-do-i-use-multiple-amd-graphic-cards"), and when I put >  lspci | grep VGA, it is only showing one :

  GPU: 01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
[/TD]
[/TR]
[/TABLE]




So I think that the aticonfig itself is not recognizing my GPU's. What should I do?
Do you think connecting dummy plugs would make a difference?

---

