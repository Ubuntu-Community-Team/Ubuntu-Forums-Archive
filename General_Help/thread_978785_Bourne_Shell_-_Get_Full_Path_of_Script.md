---
title: "Bourne Shell - Get Full Path of Script"
date: 2008-11-11
forum: General Help
---

### Post by seanmu13 on 2008-11-11
I was writing a simple bourne shell script and was wondering how you can get the full path of the script you are currently executing.

Can anybody help?

Thanks,
Sean

---

### Post by Portmanteaufu on 2008-11-11
The variable "$0" is automatically populated with the name of the script being run when it starts up. You can use: 

```
PWD=`pwd`
FULLPATH="$PWD/$0"
```

to get the full path into the variable $FULLPATH.

---

### Post by Portmanteaufu on 2008-11-11
Urgh, unintentional second post. I guess I'll take this opportunity to provide unnecessary further explanation.

When a script starts, a bunch of variables are automatically populated. The name of the script is $0, and each of the arguments to the script from the command line gets its own variable in numeric order. 

For example, in the following command: 

```

cp sourceFile destinationFile

```

$0 would be "cp"
$1 would be "sourceFile"
$2 would be "destinationFile"
etc.

As far as I know, this works up until $9, at which point you have to start using the "shift" command to read further arguments.

---

### Post by seanmu13 on 2008-11-11
Thanks for the help.

---

### Post by -Zeus- on 2008-11-11
> **Portmanteaufu said:**
> The variable "$0" is automatically populated with the name of the script being run when it starts up. You can use: 

```
PWD=`pwd`
FULLPATH="$PWD/$0"
```

to get the full path into the variable $FULLPATH.

why bother doing that when you can just do this? ```
FULLPATH=$(pwd)/$0
```

---

### Post by spibou on 2008-11-11
> **Portmanteaufu said:**
> Urgh, unintentional second post. I guess I'll take this opportunity to provide unnecessary further explanation.

When a script starts, a bunch of variables are automatically populated. The name of the script is $0, and each of the arguments to the script from the command line gets its own variable in numeric order. 

For example, in the following command: 

```

cp sourceFile destinationFile

```

$0 would be "cp"
$1 would be "sourceFile"
$2 would be "destinationFile"
etc.

As far as I know, this works up until $9, at which point you have to start using the "shift" command to read further arguments.
You don't have to use shift, you can do ${10}, ${11}, etc.

---

### Post by Portmanteaufu on 2008-11-11
> **spibou said:**
> You don't have to use shift, you can do ${10}, ${11}, etc.

Educational! Thanks.

---

### Post by spibou on 2008-11-11
> **-Zeus- said:**
> 
[QUOTE=Portmanteaufu;6152671]The variable "$0" is automatically populated with the name of the script being run when it starts up. You can use: 

```
PWD=`pwd`
FULLPATH="$PWD/$0"
```

to get the full path into the variable $FULLPATH.
why bother doing that when you can just do this? ```
FULLPATH=$(pwd)/$0
```[/QUOTE]

At the very least you need to check that $0 does not already contain a full pathname in which case you should not append $PWD in front. Even with that check it's making me a bit nervous but I can't think of a specific example where you would get the wrong result.

---

