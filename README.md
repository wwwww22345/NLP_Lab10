I adapted the lab’s LSTM model to translate English to French.
**Challenges and fixes**
- Missing text: I removed missing and empty sentence pairs to fix tokenization errors.
- Incorrect inputs: Used padded integer arrays instead of raw text for training for the Embedding layer, The variables 'eng_train' and 'frn_train' contained strings.
- Slow training: Switched to a Colab GPU, increased batch size to 64, reduced layer sizes to 32, and used 10 epochs, the training time changed from 2 hours for each epoch to less than 2 minutes each epoch.
- GPU padding error: in yy Embedding layer i used mask_zero=True, while the earlier padding placed zeros at the beginning. so I changed to padding="post" while keeping mask_zero=True.
- Unknown words: After splitting before tokenization, some test words may be absent from the training vocabulary, so i added '<OOV>' tokens and filtered them from displayed translations in inference function.
