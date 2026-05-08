# pet03186.github.io
GEOG 5543 Final: Predicting Modern Locations from Historical Plat Maps Using OCR.

The original goal of this project was to create a pipeline that would use OCR on a large sample of historical plat maps and produce GEOtiff outputs. Ultimately, it became very difficult given my limited experience with the techniques used to create a pipeline that could handle wide variations in handwriting, quality of documents, and more. Thus, this notebook is better described as an exploratory analysis/a demo of one plat to demonstrate techniques.   
>
GPU use is optional (decreases easyocr usage by ~3mins). Code cell 1 demonstrates how to check if GPU is active. Code cell 2 provides all necessary packages to run this notebook. No manual inputs are required for this notebook, and customized parameters are highlighted via comments throughout.

>

Markdown cells and code comments were incorporated so that I could separate my notebook into sections and get more granular with my documentation.  
>

AI DISCLAIMER: I utilized LLM models to troubleshoot specific issues that occurred in my pipeline and brainstorm possible approaches.  
>

*Some* of the approaches that were tried and failed or abandoned:

- The original approach was to OCR the full image, which proved difficult especially in downstream cleaning. I also tried multiple OCR packages (ex. tesseract, CRAFT) that had varying success based on my cleaning strategy. Instead, I ended up starting from a geometry perspective to simulate targeted OCR.

- I opted for maximum recall when using OCR, and cleaning the df later. When applying constraints early-on, it led to misspellings and other errors.

- Trying to append st and ave to street names (difficult, ultimately not needed based on my final location strategy)

- I dentifying control points for final bounding box (modern day intersections not present, involved manual inputs)

- various geocoders that did not work

- attempted hough/skeletonization in part 2, not beneficial in this case

>
>

Ultimately the pipeline that worked:

1. Uploading Scanned PDF of Historical Plat Image with Minimal Preprocessing
2. **Extracting Feature Geometry & Prepping for OCR
3. OCR (Easy-OCR)
4. Predicting and Visualizing Modern Spatial Proximity

**Part 2 - some of the steps involved here like creating a binary mask, line segment detection, street buffers, etc. would be beneficial in a final GeoTIFF output. Due to the complexity of filtering/designing a pipeline applicable to a wide variety of plats, time constraints, and specific features of this plat/modern day streets, this was not incorporated into the final output. It remains in the notebook to demonstrate a typical approach/visualize potential benefit, and to create the mask for our OCR (which was very helpful).  
