---
title: "&quot;Nice&quot;"
date: 2008-07-21
forum: General Help
---

### Post by pedrom169 on 2008-07-21
this may sound like a WINE question but its not haha

im am playing a game using WINE and its running a little slow.
i was speaking to the admin of the game who also uses Ubuntu 8.04 and runs the game and he said it runs like when using winblows.

he told me to use something in the terminal called "nice".
he told me to trying in "man nice" for help
but is not very much help haha

any help is apprecticated.

Peter

---

### Post by sdennie on 2008-07-21
I think it's sometimes necessary to set the wine server to nice.  You might be able to run your command like this:

```

nice normal_command_to_run_your_wine_program

```

Or, if that doesn't help, once the game is running, you could also try:

```

renice +19 `pidof wineserver`

```

---

### Post by pedrom169 on 2008-07-21
i was reading it aswell.. and it said that the numbers are from -20 to 19. with -20 making the program with most priority and 19 being less.

so if i wanted wine to have more priority would i put

```
renice -20 `pidof wineserver`
```

---

### Post by sdennie on 2008-07-21
You can try both the highest (negative numbers) and lowest (positive numbers) priorities to see which works best.  I have a feeling it will be the +19 that helps though.

---

### Post by pedrom169 on 2008-07-21
cheers mate
i will try this when i get to my ubuntu machine as i am at work.

one last thing

this code

```
nice normal_command_to_run_your_wine_program
```

whats the normal command haha.

Peter

---

### Post by mcduck on 2008-07-21
The problem here would be that only root is allowed to set nice levels smaller than 0. Normal users are only able to use nice values of 0 to 19 (making programs *slower* than normally, thus more "nice" towards other running processes).

So getting more performance would require running wine & the game as root, which doesn't sound like a smart/safe idea to me..

---

### Post by pedrom169 on 2008-07-21
what would that do? make system files vunurable for attacks or something?

---

### Post by sdennie on 2008-07-21
> **pedrom169 said:**
> cheers mate
i will try this when i get to my ubuntu machine as i am at work.

one last thing

this code

```
nice normal_command_to_run_your_wine_program
```

whats the normal command haha.

Peter

Whatever command you normally use to start your game.

> **mcduck said:**
> The problem here would be that only root is allowed to set nice levels smaller than 0. Normal users are only able to use nice values of 0 to 19 (making programs *slower* than normally, thus more "nice" towards other running processes).

So getting more performance would require running wine & the game as root, which doesn't sound like a smart/safe idea to me..

Yes, normally that's true but, in the case of wine programs, there is the actual program and then there is wineserver (I assume it's providing some Windows services that allow things to run on Linux).  By setting the wineserver to nice, you are giving preference to the actual executable and not the wine server which, in the case of games, may make a difference.

---

### Post by mcduck on 2008-07-21
> **pedrom169 said:**
> what would that do? make system files vunurable for attacks or something?

At least more vulnerable than it is now. Using minimum permissions reequired for the task is pretty much the backbone of Linux/Unix security, and running things as root gives them _full_ unlimited permissions to everything in your system.

Even if it wouldn't be security issue it would make possible software bugs affect the whole system instead of just your own user account.

---

### Post by pedrom169 on 2008-07-21
> **vor said:**
> Whatever command you normally use to start your game.

ifs its basically in applications > Wine > programms > Terra World Online> TWOReborn.exe

what would i write?

---

### Post by Tod Merley on 2008-07-21
> **pedrom169 said:**
> this may sound like a WINE question but its not haha

im am playing a game using WINE and its running a little slow.
i was speaking to the admin of the game who also uses Ubuntu 8.04 and runs the game and he said it runs like when using winblows.

he told me to use something in the terminal called "nice".
he told me to trying in "man nice" for help
but is not very much help haha

any help is apprecticated.

Peter

Hi Peter!

Your friend is correct.  The command in a terminal "man nice" will show the manual for the command "nice".

"Nice" is used to set the priority of a program running in Linux.  I use it when making MP3s for example to make sure that the MP3 encoder is not taking over all of the processor power such that browsing or whatever else is affected.  In your case you want the wine programs to take a higher priority.

Have fun!

Tod

---

