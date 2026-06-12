---
title: "Bash Aliases"
date: 2008-11-18
forum: General Help
---

### Post by ericartman_ on 2008-11-18
I want to create an alias y that will first killall x and then run x so that when I enter it into the command line it will look something like this...

"$ y x"

I may have written that in a very confusing manner....sorry about that. I guess what I'm saying is that I want to be able to run the alias with whatever I type after it as an argument for every command the alias runs.

---

### Post by geirha on 2008-11-18
You'll need to use a script for that.

```

#!/bin/sh
killall "$1"
exec "$@"

```

---

### Post by mannih2001 on 2008-11-18
You will not be able to do this with an alias. But you can resort to a function instead:

```

foo() {
    if [ "$1" != "" ]; then
        echo $1
        some_command $1
    else
        echo "missing argument to function foo"
    fi
}

```

---

