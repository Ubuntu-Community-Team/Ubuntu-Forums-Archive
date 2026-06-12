---
title: "Help with a (simple?) programming error in C"
date: 2005-12-02
forum: General Help
---

### Post by Vilhelmo on 2005-12-02
I've got this file (i think it is old) that should make my soundcard work. I need to compile it. I think it is programmed in C. Anyway, when I try "sudo make" it's just a bunch of errors showing up. I've localised the errors in the code.

This is the part of the code the compiler won't work with: 
```
char map[]="memory map:

GRPS:                  0x100-0x1FF
ITRAM Data Buffer:     0x200-0x27F
XTRAM Data Buffer:     0x280-0x29F
ITRAM Address Buffer:  0x300-0x37F
XTRAM Address Buffer:  0x380-0x39F
Program Memory:        0x400-0x600
";
```
I know it has something to do with the " signs. The program don't seem to accept that the author has written the code between the two "" on many different lines. 

So if anyone with some knowledge in C could help me correct this error I would be grateful.

---

### Post by rplantz on 2005-12-02
You cannot run strings -- things enclosed in "..." -- across lines. They must be on the same line. That is, you cannot press the return (or enter) key.

If you want the text to go to the next line, you must use the newline character, which is produced by pressing two keys -- \n

I copy and pasted your example and replaced all the visual (in the source) newlines with a \n:
```

char map[]="memory map:\n\nGRPS:                  0x100-0x1FF\nITRAM Data Buffer:     0x200-0x27F\nXTRAM Data Buffer:     0x280-0x29F\nITRAM Address Buffer:  0x300-0x37F\nXTRAM Address Buffer:  0x380-0x39F\nProgram Memory:        0x400-0x600\n";

```

I saved this in a file named junk.c (no offense  :-) ):
```

#include <stdio.h>
int main() {
char map[]="memory map:\n\nGRPS:                  0x100-0x1FF\n\
ITRAM Data Buffer:     0x200-0x27F\nXTRAM Data Buffer:     0x280-0x29F\nITRAM Address Buffer:  0x300-0x37F\nXTRAM Address Buffer:  0x380-0x39F\nProgram Memory:        0x400-0x600";
 printf("%s", map);

 return 0;
}

```
and did:
```

gcc junk.c
./a.out

```

Try it.

By the way, when I tried to copy and paste the contents of my junk.c file into the browser here, it very "kindly" replaced all my \n characters with a visual newline. So I had to edit it here. I may have missed one or two.

The line continuation character in C is \. Actually, it's an "escape" character which tells the C compiler to ignore the immediately following character. I.e., the return key. So you can make the above look better:
```

char map[]="memory map:\n\n\
GRPS:                  0x100-0x1FF\n\
ITRAM Data Buffer:     0x200-0x27F\n\
XTRAM Data Buffer:     0x280-0x29F\n\
ITRAM Address Buffer:  0x300-0x37F\n\
XTRAM Address Buffer:  0x380-0x39F\n\
Program Memory:        0x400-0x600\n";

```

---

