---
title: "Shell Script: if statement confusion"
date: 2008-10-19
forum: General Help
---

### Post by turiya on 2008-10-19
I have some experience in writing shell scripts but I've never made one that involved the if statement. The effect I'm trying to go for is to check to see if an environment variable, in this case "RANDOMIZED", is set to the current date in %Y%m%d%H format.

The two problems I'm encountering are:
1. I can't figure out how to actually set an environment variable to the value of the date. Probably just tiredness for this one.
2. Never having used the if statement I cannot figure out how to check if a variable is equal to the date.

Any help would be appreciated.

---

### Post by MakotoTheKnight on 2008-10-19
I don't know much about the environment, but from what I do remember about if statements:

if [ statement ]; then

     //actions to perform
fi

I believe the else if statement is accomplished with elif, but I can't recall.  Hope I was able to help.

---

### Post by turiya on 2008-10-19
I probably should have mentioned that I know the basics of how the if statement works, but my experience in programming led me to believe that the check would involve an '==' symbol. When the script is run the terminal informs me that this is not the correct syntax. I mostly need the syntax for the condition to check if "VARIABLE == date" with date in the format of %Y%m%d%H. Or more correctly "VARIABLE != date".

---

### Post by bodhi.zazen on 2008-10-19
I think it would help if you gave a better description of what you are trying to accomplish or posted a fragment of your script you need help with.

You can print a list of environmental variables with :

```
printenv
```

I did not see an environmental variable with the date on my system.

To set a variable, declare it. To use it in your shell export it from .bashrc

add something like

export DATE=`/bin/date`

but you would need to update that somehow as that would show the time the shell was started.

---

### Post by turiya on 2008-10-19
> **bodhi.zazen said:**
> I think it would help if you gave a better description of what you are trying to accomplish or posted a fragment of your script you need help with.

I'll try to explain it better...

Basically what I have is a shell script that is run once upon startup and a similar script that I can run manually. The scripts are designed to randomize my desktop background and a few of my system sounds. Up to this point I had been seeding the random number generator every time I started up the script. This creates a situation where I end up seeing certain desktop backgrounds set fairly often. What I want is a way of checking whether the script had been run recently and if it had then don't re-seed the random number generator. If it hadn't been run in a while then I would seed the random number generator. Or, for a slightly better way of running, check to see whether the script had been run since I logged in and if it had don't re-seed, and if it hadn't then re-seed.

---

