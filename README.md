# Blackjack: The Science of Winning

## Overview
This project analyzes the game of blackjack using a dataset generated from a realistic simulator that follows the most common Las Vegas casino rules. The objective is to investigate statistical patterns and validate strategies, particularly the effectiveness of the Hi-Lo card counting system.

## Authors
- Zakharii Tepliakov
- Danyil Ikonnikov
- Stanislav Vus

## Dataset
The dataset includes simulated blackjack rounds with the following key features:

- **shoe_id**: Identifier for the shoe
- **cards_remaining**: Number of cards remaining at the start of a round
- **dealer_up**: Dealer's visible card
- **initial_hand**: Player's starting two cards
- **dealer_final**: Dealer's final hand
- **dealer_final_value**: Dealer's final hand value
- **player_final**: Player's final hand(s)
- **player_final_value**: Player's final hand value(s)
- **actions_taken**: Sequence of actions taken by the player
- **run_count**: Count according to the Hi-Lo system
- **true_count**: Adjusted Hi-Lo count
- **win**: Amount won or lost per round

A new variable, **win_category**, is added to classify outcomes as **Win**, **Loss**, or **Draw**.

## Hypothesis Testing

### Hypothesis 1: Effectiveness of the Hi-Lo System

**Null Hypothesis ($H_0$):** There is no significant difference in the mean run count between won and lost games.

**Alternative Hypothesis ($H_1$):** The mean run count is higher in won games than in lost games.

A **t-test** was conducted after confirming normality assumptions. Results indicate a significantly higher mean run count in won games, supporting the effectiveness of card counting.

### Hypothesis 2: Impact of the Dealer's Upcard

**Null Hypothesis ($H_0$):** The dealer’s upcard (10 or Ace) does not affect the likelihood of winning.

**Alternative Hypothesis ($H_1$):** Players are more likely to lose when the dealer's upcard is 10 or Ace.

A **chi-squared test for independence** was performed, revealing a strong relationship between dealer upcards and losing probability. The null hypothesis was rejected.

### Hypothesis 3: Influence of Shoe Size on Winning Probability

**Null Hypothesis ($H_0$):** The number of decks in the shoe does not affect the player's chances of winning.

**Alternative Hypothesis ($H_1$):** The number of decks influences win probability.

A **logistic regression model** was built to test this relationship. The model indicated that the size of the shoe does not have a significant impact on winning chances, failing to reject the null hypothesis.

## Data Processing

Data cleaning and transformation steps include:
- Expanding hands when the player splits, treating each split as a separate observation.
- Replacing 'BJ' (Blackjack) with numerical values.
- Adjusting win amounts proportionally when splits occur.
- Creating a categorical variable for dealer upcards (10/Ace vs. others).

## Visualization

Several plots illustrate key relationships:
- **Mean run count by win category**: Shows higher counts in won games.
- **Distribution and Q-Q plots**: Assess normality of run count.
- **Chi-squared contingency tables**: Examine dependencies between dealer upcard and win/loss outcomes.
- **Logistic regression coefficients**: Interpret how shoe size influences winning probability.

## Conclusion
The analysis confirms that:
- The Hi-Lo system correlates with better outcomes.
- A dealer upcard of 10 or Ace significantly increases the likelihood of losing.
- The number of decks used in the shoe does not significantly impact win probability.

## Requirements
To run the analysis, install the following R packages:
```r
install.packages(c("ggplot2", "dplyr", "magrittr", "stringr", "tidyr"))
```