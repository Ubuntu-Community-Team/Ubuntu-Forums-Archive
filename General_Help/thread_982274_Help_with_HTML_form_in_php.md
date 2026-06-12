---
title: "Help with HTML form in php"
date: 2008-11-14
forum: General Help
---

### Post by Mercedes300 on 2008-11-14
The problem is that I have a php script that uses a HTML form.  When the submit button is clicked, the page cycles, but the data is not displayed.  Here is the code:

<?php
 printf('<form action="%s" method="post" name="PickQuantity">', $PHP_SELF);
 phpinfo();
?>
             I would like to have
             <SELECT NAME="IHL_Quantity">
               <OPTION SELECTED>Select Quantity
                       <OPTION>01<OPTION>02<OPTION>03<OPTION>04<OPTION>05<OPTION>06<OPTION>07<OPTION>08<OPTION>09<OPTION>10
                       <OPTION>11<OPTION>12<OPTION>13<OPTION>14<OPTION>15<OPTION>16<OPTION>17<OPTION>18<OPTION>19<OPTION>20
                       <OPTION>21<OPTION>22<OPTION>23<OPTION>24<OPTION>25<OPTION>26<OPTION>27<OPTION>28<OPTION>29<OPTION>30
           <OPTION>50<OPTION>100
             </SELECT>
             copies.
             <br><br><br>
             <p align='right'>
               <input type="Submit" name="submit_quantity" value="Continue" align="center">
              </p>
</form>
<?php
 printf('<BR><BR>The Quantity is:  %s<br><br>', $IHL_Quantity);
?>

I'm running Apache and PHP on my local machine.  Other php scripts have worked fine, but they do not involve HTML <form> tags.

Please, if anyone can help, I'm taring my hair out over this one! :mad:

---

### Post by Botnix on 2008-11-14
I'm having the same problem.

Any help would be greatly appreciated.

---

### Post by smlefo on 2008-11-14
You probably don't have register_globals on (which is good).

You should be using:

$_POST['IHL_Quantity'] instead of $IHL_Quantity

i.e.:

printf('<BR><BR>The Quantity is: %s<br><br>', $_POST['IHL_Quantity']);

---

### Post by Botnix on 2008-11-15
Dear SMELFO,

I used the $_POST['variable name'] construct, but it still doesn't work.  It reloads the page upon clicking the SUBMIT button, but does not display the variable assigned by the SELECT tag.

Any other suspects?

Thanks for taking the time to look at this problem.

Regards,

b

---

### Post by smlefo on 2008-11-15
Hmm... this is how I would write it:

[PHP]
<html>
<body>
<form method="post" action="<?= $_SERVER['PHP_SELF'] ?>">
<select name="test">
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
<option value="5">5</option>
</select><br />
<input type="submit" value="Go" />
</form>
<?
if (isset($_POST['test']))
{
?>
<p>
The form was submitted with the value <?= $_POST['test'] ?>.
</p>
<?
}
?>
</body>
</html>
[/PHP]

---

### Post by Botnix on 2009-02-21
Thanks to smlefo, but I'm still having a problem with the most basic php scripts.  I changed the php.ini file from the initial to php.ini-recommended in order to make the site live, but still nothing but the simplest 'Hello World' type of script will run.

The php.ini file is running in the directory with the script but no dice.

I'm running v.8.04 and php version 5.2.4-2ubuntu5.5.

I would like to avoid using $_SERVER and $_POST in front of every variable as this would require a tedious re-write of legacy code.  Is there a way to turn off this requirement?

Any help would be greatly appreciated.

---

### Post by Botnix on 2009-02-21
I'm currently reading [http://wiki.lunarpages.com/PHP_and_Register_Global_Variables](http://wiki.lunarpages.com/PHP_and_Register_Global_Variables) which is an update for old php coders like me.  If this is the state of the world, I'll have to play along.

---

