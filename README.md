I built a translation model using a small dataset, finding 161 unique English
words and 248 unique Swedish words since Swedish is morphologically much more
complex. 

Because there were so few words and no punctuation, I built my own
lil tokenizer instead of using a tokenizer like spaCy. 
For the architecture, I chose GRU! They efficiently capture sequential
dependencies with fewer parameters than LSTMs, making them faster to train and
less prone to overfitting on a small dataset. 

Training was pretty nice, reaching a perplexity of 1.007 by epoch 10, 
meaning the model had basically 0 percent confusion and was 100 percent
certain of the correct Swedish word at every step. It practically generalized
the grammar and vocab perfectly without overfitting! I did a lil sanity check
translating a red apple is hot to ett rött äpple är hett, which was correct.

I initially got a SacreBLEU score of 0.00 because of a dictionary unpacking bug,
but after fixing it, the model scored an amazing 99.56.

The detailed evaluation metrics showed the model generated exactly 7285 words
to perfectly match the reference length, resulting in a flawless brevity 
penalty of 1.0. It was essentially recreating exact 4-word phrases with 99.3
percent accuracy, proving the model crushed this microlang translation task.