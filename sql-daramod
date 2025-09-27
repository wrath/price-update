UPDATE wp_postmeta AS pm
JOIN (
    -- انتخاب محصولات ساده
    SELECT DISTINCT tr.object_id AS product_id
    FROM wp_term_relationships AS tr
    JOIN wp_term_taxonomy AS tt ON tr.term_taxonomy_id = tt.term_taxonomy_id
    JOIN wp_terms AS t ON tt.term_id = t.term_id
    WHERE tt.taxonomy = 'product_cat'
      AND t.name IN (
        'لباس ورزشی',
        'سوتین ورزشی',
        'شلوار ورزشی',
        'ویکتوریا سکرت',
        'آرایشی',
        'اسکراب بدن',
        'بادی لوشن',
        'بادی میست',
        '236 میلی لیتر',
        '250 میلی لیتر',
        '355 میلی لیتر',
        '75 میلی لیتر',
        'برنز کننده',
        'روغن بدن',
        'زیبایی صورت',
        'براق کننده لب',
        'حجم دهنده لب',
        'عطر',
        '100 میلی لیتر',
        '50 میلی لیتر',
        'جیبی 7 میلی لیتر',
        'کره بدن',
        'اکسسوری',
        'آویز',
        'پتو',
        'جاکارتی',
        'دمپایی رو فرشی',
        'کیف',
        'کیف پول',
        'کیف لوازم آرایشی',
        'بیکینی و مایو',
        'بیکینی',
        'مایو',
        'پتو و بلنکت',
        'پک کادویی',
        'لباس زیر',
        'سوتین',
        'شورت'
    )
    UNION
    -- انتخاب محصولات متغیر
    SELECT DISTINCT p.ID AS product_id
    FROM wp_posts p
    JOIN wp_term_relationships tr ON p.post_parent = tr.object_id
    JOIN wp_term_taxonomy AS tt ON tr.term_taxonomy_id = tt.term_taxonomy_id
    JOIN wp_terms AS t ON tt.term_id = t.term_id
    WHERE p.post_type = 'product_variation'
      AND t.name IN (
        'لباس ورزشی',
        'سوتین ورزشی',
        'شلوار ورزشی',
        'ویکتوریا سکرت',
        'آرایشی',
        'اسکراب بدن',
        'بادی لوشن',
        'بادی میست',
        '236 میلی لیتر',
        '250 میلی لیتر',
        '355 میلی لیتر',
        '75 میلی لیتر',
        'برنز کننده',
        'روغن بدن',
        'زیبایی صورت',
        'براق کننده لب',
        'حجم دهنده لب',
        'عطر',
        '100 میلی لیتر',
        '50 میلی لیتر',
        'جیبی 7 میلی لیتر',
        'کره بدن',
        'اکسسوری',
        'آویز',
        'پتو',
        'جاکارتی',
        'دمپایی رو فرشی',
        'کیف',
        'کیف پول',
        'کیف لوازم آرایشی',
        'بیکینی و مایو',
        'بیکینی',
        'مایو',
        'پتو و بلنکت',
        'پک کادویی',
        'لباس زیر',
        'سوتین',
        'شورت'
    )
) AS filtered_products ON pm.post_id = filtered_products.product_id
SET pm.meta_value = ROUND(CAST(pm.meta_value AS DECIMAL(10, 2)) * 1.10, 0)
WHERE pm.meta_key IN ('_regular_price', '_sale_price', '_price')
  AND pm.meta_value REGEXP '^[0-9]+(\.[0-9]+)?$';
