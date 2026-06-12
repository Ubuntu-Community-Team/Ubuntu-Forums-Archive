---
title: "How do I use C?"
date: 2008-11-24
forum: General Help
---

### Post by raunchyrex on 2008-11-24
Hey guys,
I started learning 'C' programming language in Windows platform. In windows I can code a program by opening an editor like "Borland Turbo C." I can code, compile, run and save using it.
Is there any such software for Ubuntu? If yes, what is it? If no, how do I achieve that functionality???

---

### Post by Washer on 2008-11-24
er.. get [apt:build-essential]("apt:build-essential") & i guess try [netbeans]("apt:netbeans")

Never tried it though. I'm doing some light C work & I have to use makefiles so good luck.

---

### Post by rakris on 2008-11-24
IDE- go for Anjuta

---

### Post by ju2wheels on 2008-11-24
To install the C compiler:

```

sudo apt-get install build-essential gcc libc6

```

You can use any text editor, however most people use vim or emacs. For a beginner, those might have steep learning curves and also dont have auto complete. Kate is simpler, has color coding but no auto complete (to my knowledge). You can also try Anjuta and Eclipse for full IDE environments.

Either way, whatever editor you use, simply save your C file somewhere and if you are not using an IDE then this is how you compile it from the command line:

```

gcc -Wall -o output_name.exe code_file.c
./output_name.exe

```

The above compiles code_file.c and names the compiled executable output_name.exe (note that you dont have to add .exe like you do in Windows, but thats up to your preference). If you dont specify (-o output_name.exe) the executable is named a.out (IIRC). The second line runs your compiled program.

---

### Post by sambarusty on 2008-11-24
very easy, most unix/linux platforms have a c compiler cc/gcc or cc softlinked to gcc depending where you are, then you can compile your c program cc cprogram.c -o somname -I/include directories -L/library directories -llibs to include.  good luck

---

### Post by sambarusty on 2008-11-24
I don't think I have ever had to explicitly install the compiler, I would try just doing a cc or gcc and see if you get a complaint about no input files in which case it is installed.

---

