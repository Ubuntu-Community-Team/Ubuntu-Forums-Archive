---
title: "Issues with Stone soup Installation"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by spiritfox on 2008-12-24
I've been trying to install Dungeon Crawl Stone Soup 0.4.4.  I've installed the latest version of build-essential, the latest version of bison, and the latest version of flex.  I get the following errors when running make:

```
libunix.cc:81:24: error: curses.h: No such file or directory
libunix.cc:89: error: ‘COLOR_PAIR’ was not declared in this scope
libunix.cc:93: error: ‘WINDOW’ was not declared in this scope
libunix.cc:93: error: ‘w’ was not declared in this scope
libunix.cc:93: error: expected primary-expression before ‘const’
libunix.cc:93: error: initializer expression list treated as compound expression
libunix.cc: In function ‘unsigned int convert_to_curses_attr(int)’:
libunix.cc:101: error: ‘A_STANDOUT’ was not declared in this scope
libunix.cc:102: error: ‘A_BOLD’ was not declared in this scope
libunix.cc:103: error: ‘A_BLINK’ was not declared in this scope
libunix.cc:104: error: ‘A_UNDERLINE’ was not declared in this scope
libunix.cc:105: error: ‘A_REVERSE’ was not declared in this scope
libunix.cc:106: error: ‘A_DIM’ was not declared in this scope
libunix.cc:107: error: ‘A_NORMAL’ was not declared in this scope
libunix.cc: In function ‘short int translate_colour(short int)’:
libunix.cc:122: error: ‘COLOR_BLACK’ was not declared in this scope
libunix.cc:124: error: ‘COLOR_BLUE’ was not declared in this scope
libunix.cc:126: error: ‘COLOR_GREEN’ was not declared in this scope
libunix.cc:128: error: ‘COLOR_CYAN’ was not declared in this scope
libunix.cc:130: error: ‘COLOR_RED’ was not declared in this scope
libunix.cc:132: error: ‘COLOR_MAGENTA’ was not declared in this scope
libunix.cc:134: error: ‘COLOR_YELLOW’ was not declared in this scope
libunix.cc:136: error: ‘COLOR_WHITE’ was not declared in this scope
libunix.cc: In function ‘void setup_colour_pairs()’:
libunix.cc:167: error: ‘init_pair’ was not declared in this scope
libunix.cc:171: error: ‘COLOR_BLACK’ was not declared in this scope
libunix.cc:171: error: ‘init_pair’ was not declared in this scope
libunix.cc: In function ‘int getch_ck()’:
libunix.cc:314: error: ‘KEY_BACKSPACE’ was not declared in this scope
libunix.cc:315: error: ‘KEY_DC’ was not declared in this scope
libunix.cc:316: error: ‘KEY_HOME’ was not declared in this scope
libunix.cc:317: error: ‘KEY_PPAGE’ was not declared in this scope
libunix.cc:318: error: ‘KEY_END’ was not declared in this scope
libunix.cc:319: error: ‘KEY_NPAGE’ was not declared in this scope
libunix.cc:320: error: ‘KEY_UP’ was not declared in this scope
libunix.cc:321: error: ‘KEY_DOWN’ was not declared in this scope
libunix.cc:322: error: ‘KEY_LEFT’ was not declared in this scope
libunix.cc:323: error: ‘KEY_RIGHT’ was not declared in this scope
libunix.cc: At global scope:
libunix.cc:365: error: expected initializer before ‘*’ token
libunix.cc: In function ‘void setup_message_window()’:
libunix.cc:368: error: ‘Message_Window’ was not declared in this scope
libunix.cc:369: error: ‘newwin’ was not declared in this scope
libunix.cc:379: error: ‘scrollok’ was not declared in this scope
libunix.cc:380: error: ‘idlok’ was not declared in this scope
libunix.cc: In function ‘void clear_message_window()’:
libunix.cc:391: error: ‘Message_Window’ was not declared in this scope
libunix.cc:391: error: ‘wattrset’ was not declared in this scope
libunix.cc:392: error: ‘werase’ was not declared in this scope
libunix.cc:393: error: ‘wrefresh’ was not declared in this scope
libunix.cc: In function ‘void message_out(int, int, const char*, int, bool)’:
libunix.cc:399: error: ‘Message_Window’ was not declared in this scope
libunix.cc:399: error: ‘wattrset’ was not declared in this scope
libunix.cc:406: error: ‘wmove’ was not declared in this scope
libunix.cc:407: error: ‘waddstr_with_altcharset’ cannot be used as a function
libunix.cc:412: error: ‘getyx’ was not declared in this scope
libunix.cc:413: error: ‘scroll’ was not declared in this scope
libunix.cc:421: error: ‘getyx’ was not declared in this scope
libunix.cc:422: error: ‘move’ was not declared in this scope
libunix.cc:425: error: ‘wrefresh’ was not declared in this scope
libunix.cc: In function ‘void unixcurses_startup()’:
libunix.cc:463: error: ‘initscr’ was not declared in this scope
libunix.cc:464: error: ‘raw’ was not declared in this scope
libunix.cc:467: error: ‘nonl’ was not declared in this scope
libunix.cc:468: error: ‘stdscr’ was not declared in this scope
libunix.cc:468: error: ‘FALSE’ was not declared in this scope
libunix.cc:468: error: ‘intrflush’ was not declared in this scope
libunix.cc:470: error: ‘TRUE’ was not declared in this scope
libunix.cc:470: error: ‘keypad’ was not declared in this scope
libunix.cc:473: error: ‘ESCDELAY’ was not declared in this scope
libunix.cc:477: error: ‘meta’ was not declared in this scope
libunix.cc:478: error: ‘start_color’ was not declared in this scope
libunix.cc:481: error: ‘scrollok’ was not declared in this scope
libunix.cc: In function ‘void unixcurses_shutdown()’:
libunix.cc:491: error: ‘Message_Window’ was not declared in this scope
libunix.cc:493: error: ‘delwin’ was not declared in this scope
libunix.cc:498: error: ‘endwin’ was not declared in this scope
libunix.cc: In function ‘int itoa(int, char*, int)’:
libunix.cc:556: error: ‘OK’ was not declared in this scope
libunix.cc: In function ‘int cprintf(const char*, ...)’:
libunix.cc:569: error: ‘stdscr’ was not declared in this scope
libunix.cc:569: error: ‘waddstr_with_altcharset’ cannot be used as a function
libunix.cc:570: error: ‘refresh’ was not declared in this scope
libunix.cc: At global scope:
libunix.cc:577: error: redefinition of ‘int waddstr_with_altcharset’
libunix.cc:93: error: ‘int waddstr_with_altcharset’ previously defined here
libunix.cc:577: error: ‘WINDOW’ was not declared in this scope
libunix.cc:577: error: ‘w’ was not declared in this scope
libunix.cc:577: error: expected primary-expression before ‘const’
libunix.cc:89: warning: ‘Current_Colour’ defined but not used
libunix.cc:91: warning: ‘int curs_fg_attr(int)’ declared ‘static’ but never defined
libunix.cc:92: warning: ‘int curs_bg_attr(int)’ declared ‘static’ but never defined
libunix.cc:95: warning: ‘cursor_is_enabled’ defined but not used
libunix.cc:97: warning: ‘unsigned int convert_to_curses_attr(int)’ defined but not used
libunix.cc:117: warning: ‘short int translate_colour(short int)’ defined but not used
make[1]: *** [libunix.o] Error 1
make[1]: Leaving directory `/home/tauntaun/Desktop/stone_soup-0.4.4-src/source'
make: *** [all] Error 2

```

I would assume those errors sprung from the missing "curses.h," but I don't know if that's a standard library or is supposed to be provided.

---

### Post by spiritfox on 2008-12-24
nvm, found the solution at [http://www.cyberciti.biz/faq/linux-error-cursesh-no-such-file-directory/](http://www.cyberciti.biz/faq/linux-error-cursesh-no-such-file-directory/)
Thanks anyway!

---

