# serendipity-machine
A little PHP to promote spontaneous discovery (from a pre-selected set).

##Synopsis
This tool uses PHP to select a random XML file from a list, then simplexml_load_file to load and read the file and extract portions. This was developed as a fun and quirky discovery tool for a library. 

##How to Use This
This repository includes a php file, and three dummy XML-EAD files (populated with dummy text from http://libipsum.com/). The Serendipidity Machine can be dropped on a server running PHP and it should be ready to go. It'll be more interesting, of course, if you replace the dummy files with files promoting your library's collections.

###Basid Code
The Serendipity Machine uses '''array_rand''' to choose a selection from a list.
```
    <?php
  		$input = array(
  		//list of options here, within quotes and seperated by commas
  		"OptionOne", "OptionTwo", "OptionThree", "OptionFour", "OptionFive"
  		
  		);
  		$rand_keys = array_rand($input, 2);
		?>
```

The Serendipity Machine takes this one step further by customizing the output for XML-EAD finding aids. 

###Randomizing and Retrieving EAD Elements
Using the simplexml_load_file, we extract what we need for the XML-EAD file. 

```
<?php
		$input = array(
	$input = array(
		//list of options here, within quotes and seperated by commas
		"OptionOne", "OptionTwo", "OptionThree", "OptionFour", "OptionFive"

		);
		$rand_keys = array_rand($input, 2);
		
		
		//let's echo out the Collection Name, Abstract and Call Number
		echo "<div id='serendipity'>"  .  "<p>" . "<strong>"  .  $xml->archdesc->did->unittitle . "</strong>" . "</p>" . "<p>" . $xml->archdesc->did->abstract .  "</p>"   . "View full finding aid: ". "<a href='http://www.amphilsoc.org/collections/view?docId=ead/" . $input[$rand_keys[0]] ."-ead.xml" . "' target='new'>" . $input[$rand_keys[0]] . "</a>" .  "</div>" . "\n";
		
		
		
		?>

```

