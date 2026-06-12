---
title: "Strage behavior of keyboard in ubuntu 10.04LTS."
date: 2012-03-06
forum: Hardware
---

### Post by arroy_0209 on 2012-03-06
In my ubuntu 10.04 LTS, there is a new problem I am facing. Suppose I give the command on terminal: sudo netstat -anlp |more. This has a lengthy output, to be read scrolling over terminal. When I hit enter, first a full screen of output is displayed and the last line contains the word: "more" asking me to hit space bar to see the next screenful of output or hit enter to see the nest line of output etc. If I press "q", I should come out of the results and get back the terminal prompt. This is the familiar behavior. But at present the spacebar does not work at all when "more" has appeared. If I press "enter" repeatedly, somehow I can manage to reach the end of the result but pressing "enter" repeatedly after that does not give usual terminal prompt vertically, but gives horizontally. That is, I am getting:
```

abc@abc-desktop:~$abc@abc-desktop:~$abc@abc-desktop:~$abc@abc-desktop:~$abc@abc-desktop:~$

```instead of getting:
```

abc@abc-desktop:~$
abc@abc-desktop:~$
abc@abc-desktop:~$
abc@abc-desktop:~$
abc@abc-desktop:~$

```Moreover while getting prompt horizontally, if I use some command like "ls", the command is not visible on the terminal but the result is visible. Sometimes it seems just before "ls" the terminal had accepted some other command like opening a pdf file with evince etc (which of course I did not ask to do). I have not faced such problem before in linux or windows. Where is the problem? Is it a kind of linux virus? 
I had chosen the default keyboard type shown to me at the time of installing ubuntu (some ps/2 usa-type, if I remember correctly) few months ago. Please suggest what I should do about it. Thanks.

---

### Post by dandnsmith on 2012-03-07
It sounds as if the ouptut from the command contains a control sequence which gets the terminal into a 'funny' mode. It isn't the keyboard itself which is the problem.
It has been a good while since I have seen one of these.
I suggest you need to find an alternative way of displaying  the output (I'd use vi, and issue the command as :r! netstat -anlp)
HTH

---

