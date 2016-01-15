### Overview ###
jspos is a Javascript port of [Mark Watson's FastTag](http://www.markwatson.com/opensource/) part of speech tagger (itself based on Eric Brill's work).  jspos also includes a simple lexer for splitting a text string into words and other taggable tokens.

You can use jspos to take some text like this:

"This is some sample text. This text can contain multiple sentences."

and get back tagged words like this:

This /DT
is /VBZ
some /DT
sample /NN
text /NN
. /.
This /DT
text /NN
can /MD
contain /VB
multiple /JJ
sentences /NNS
. /.

### Sample Code ###
```
var words = new Lexer().lex("This is some sample text. This text can contain multiple sentences.");
var taggedWords = new POSTagger().tag(words);
for (i in taggedWords) {
    var taggedWord = taggedWords[i];
    var word = taggedWord[0];
    var tag = taggedWord[1];
    print(word + " /" + tag);  // if running in a browser, try document.writeln() instead of print() 
}
```

jspos should be fast enough for many uses - on V8 (Chrome's Javascript Engine), jspos can lex and tag 767 words in around 10 milliseconds (on my MacBook non-pro).

### News ###
June 13 2011 - Version 0.2 has been released, incorporating a compressed lexicon courtesy of Toby Rahilly.